# IECBXVI
// Site Católico Bonito e Pronto para Publicação


import React, { useState } from "react";


function Card({ children }) {
  return <div className="bg-white rounded-2xl shadow p-6">{children}</div>;
}

function Button({ children, className = "", ...props }) {
  return (
    <button
      className={`bg-amber-700 hover:bg-amber-800 text-white px-4 py-2 rounded-lg ${className}`}
      {...props}
    >
      {children}
    </button>
  );
}

function Home({ navigateTo }) {
  const [quote] = useState("\"Nada te perturbe, nada te espante, quem a Deus tem, nada lhe falta.\" – Santa Teresa de Ávila");

  return (
    <div className="min-h-screen bg-neutral-100 text-neutral-900 p-4 space-y-6">
      <header className="text-center py-6">
        <h1 className="text-4xl font-bold text-amber-800">IECBXVI</h1>
        <p className="text-lg italic mt-2">Blog Católico & Loja de Devoção & Plataforma de curso</p>
        <nav className="mt-4 space-x-4">
          <button onClick={() => navigateTo("home")} className="text-amber-700 hover:underline">Início</button>
          <button onClick={() => navigateTo("blog")} className="text-amber-700 hover:underline">Blog</button>
          <button onClick={() => navigateTo("loja")} className="text-amber-700 hover:underline">Loja</button>
        </nav>
      </header>

      <section className="bg-white rounded-2xl shadow p-6">
        <h2 className="text-2xl font-semibold text-amber-700 mb-4">Frase do Dia</h2>
        <p className="text-lg">{quote}</p>
      </section>

      <section className="grid grid-cols-1 md:grid-cols-2 gap-6">
        <Card>
          <h3 className="text-xl font-semibold text-amber-700">Últimos Artigos</h3>
          <ul className="mt-4 space-y-2">
            <li>📖 A humildade segundo Santo Tomás</li>
            <li>🌹 A infância espiritual de Santa Teresinha</li>
            <li>🕊️ Como rezar com os Padres da Igreja</li>
          </ul>
          <Button className="mt-4" onClick={() => navigateTo("blog")}>Ver blog</Button>
        </Card>

        <Card>
          <h3 className="text-xl font-semibold text-amber-700">Loja Devocional</h3>
          <ul className="mt-4 space-y-2">
            <li>📚 Livros espirituais</li>
          </ul>
          <Button className="mt-4" onClick={() => navigateTo("loja")}>Ir para loja</Button>
        </Card>
      </section>

      <footer className="text-center text-sm text-neutral-500 py-6">
        © 2025 IECBXI . Todos os direitos reservados.
      </footer>
    </div>
  );
}

function BlogPage({ navigateTo }) {
  return (
    <div className="p-6">
      <h2 className="text-3xl font-bold text-amber-800 mb-4">Blog Católico</h2>
      <ul className="space-y-4">
        <li><strong>A humildade segundo Santo Tomás</strong> – Um estudo profundo sobre a virtude da humildade.</li>
        <li><strong>A infância espiritual de Santa Teresinha</strong> – Como confiar totalmente em Deus.</li>
        <li><strong>Como rezar com os Padres da Igreja</strong> – Introdução à oração patrística.</li>
      </ul>
      <Button className="mt-6" onClick={() => navigateTo("home")}>Voltar</Button>
    </div>
  );
}

function StorePage({ navigateTo }) {
  return (
    <div className="p-6">
      <h2 className="text-3xl font-bold text-amber-800 mb-4">Loja Devocional</h2>
      <ul className="space-y-4">
       .
        <li><strong>Livros espirituais</strong> – Obras de santos e doutores da Igreja.</li>
        
      </ul>
      <Button className="mt-6" onClick={() => navigateTo("home")}>Voltar</Button>
    </div>
  );
}

export default function App() {
  const [page, setPage] = useState("home");

  const renderPage = () => {
    if (page === "blog") return <BlogPage navigateTo={setPage} />;
    if (page === "loja") return <StorePage navigateTo={setPage} />;
    return <Home navigateTo={setPage} />;
  };

  return (
    <div>
      {renderPage()}
    </div>
  );
}
