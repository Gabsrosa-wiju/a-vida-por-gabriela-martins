# a-vida-por-gabriela-martins

import { useMemo, useState } from "react"; import { BookOpen, Feather, Heart, Mail, MessageCircleHeart, MoonStar, ScrollText, Search, Sparkles, Users } from "lucide-react";

export default function BookPortalSite() { const [search, setSearch] = useState("");

const featuredBooks = [ { title: "Entre Marés e Destinos", genre: "Romance • Fantasia • Drama", chapters: 12, status: "Em andamento", cover: "🌊", blurb: "Uma história costurada por fios dourados, ausências que ainda respiram e encontros que parecem escritos antes do nascimento do mundo.", }, { title: "Festival de Yndara", genre: "Mistério • Romance • Realismo mágico", chapters: 7, status: "Novo capítulo em breve", cover: "🎭", blurb: "Uma vila em festa, sonhos com cheiro de presságio e personagens que tropeçam no destino como quem acende vela sem saber o que vai invocar.", }, { title: "Viridara", genre: "Fantasia • Profecia • Tensão romântica", chapters: 9, status: "Atualizado esta semana", cover: "🕊️", blurb: "Águas sagradas, segredos guardados por anciãs e um amor cercado por profecias que mordem devagar.", }, { title: "Helena e o Projeto Final", genre: "Suspense • Romance • Novela dramática", chapters: 5, status: "Em ascensão", cover: "🏛️", blurb: "Arquitetura, desejo e uma verdade enterrada debaixo da planta perfeita. Todo corredor parece esconder um batimento culpado.", }, ];

const latestChapters = [ { book: "Entre Marés e Destinos", chapter: "Capítulo 12 • A Árvore que Sonhava", date: "10 de março", excerpt: "Naquela noite, o vento parecia guardar nomes antigos no bolso, como se a ilha inteira soubesse do reencontro antes deles.", }, { book: "Festival de Yndara", chapter: "Capítulo 4 • O Teatro das Sombras", date: "06 de março", excerpt: "Quando a cortina subiu, não foi só a peça que começou. Algo muito mais antigo abriu os olhos junto com os aplausos.", }, { book: "Viridara", chapter: "Capítulo 9 • O Nome Enterrado na Água", date: "03 de março", excerpt: "Serel ouviu o próprio destino respirar atrás dela, como um bicho ferido aprendendo a voltar para casa.", }, { book: "Helena e o Projeto Final", chapter: "Capítulo 5 • Linhas Tortas Sob a Terra", date: "28 de fevereiro", excerpt: "Helena percebeu que certos segredos não gritam. Eles desenham a própria planta e esperam ser descobertos pelo erro de alguém.", }, ];

const communities = [ { title: "Leitores da Lua Alta", desc: "Para quem lê de madrugada, coleciona trechos favoritos e sente que capítulo bom não termina, só assombra bonito.", members: "2.4k leitores", icon: MoonStar, }, { title: "Teorias, Fios & Presságios", desc: "Espaço para ligar pistas, discutir suspeitos, montar mapas emocionais e delirar com classe sobre o próximo capítulo.", members: "1.1k teóricos", icon: Sparkles, }, { title: "Cartas de Coração Aberto", desc: "Mensagens dos leitores, relatos, surtos, choros elegantes e aquele bilhete que parece ter sido dobrado quatro vezes antes de chegar.", members: "980 cartas", icon: Mail, }, ];

const highlightedLetters = [ { title: "Carta da semana", author: "Assinada por uma leitora insone", text: "Eu vim por curiosidade e fiquei porque suas histórias têm perfume de verão triste com promessa de milagre. Li um capítulo e, quando vi, já estava discutindo teoria comigo mesma na cozinha.", }, { title: "Recado em destaque", author: "Do clube dos leitores noturnos", text: "Tem algo no jeito como você escreve desejo e silêncio que deixa tudo aceso. Não é só romance. É vertigem com página virada.", }, ];

const theories = [ "O Senhor dos Destinos enxerga mais do que revela, e o silêncio dele pode ser o verdadeiro aviso.", "A árvore ancestral não une apenas almas. Ela acorda memórias que ainda não aconteceram.", "Morvahar pode ser a resposta errada para a pergunta certa, e isso muda tudo.", "Helena já tocou o segredo antes, só ainda não reconheceu o desenho da própria intuição.", ];

const filteredBooks = useMemo(() => { const term = search.toLowerCase().trim(); if (!term) return featuredBooks;

return featuredBooks.filter(
  (book) =>
    book.title.toLowerCase().includes(term) ||
    book.genre.toLowerCase().includes(term) ||
    book.blurb.toLowerCase().includes(term)
);

}, [search]);

return ( <div className="min-h-screen bg-[#120d12] text-[#f7efe8]"> <header className="relative overflow-hidden border-b border-white/10 bg-[radial-gradient(circle_at_top,_rgba(244,180,145,0.20),_transparent_32%),radial-gradient(circle_at_right,_rgba(209,120,163,0.18),_transparent_22%),linear-gradient(180deg,_#20131f_0%,_#120d12_72%)]"> <div className="absolute inset-0 opacity-20"> <div className="absolute left-10 top-10 h-40 w-40 rounded-full bg-rose-200 blur-3xl" /> <div className="absolute bottom-0 right-0 h-56 w-56 rounded-full bg-amber-200 blur-3xl" /> </div>

<div className="relative mx-auto max-w-7xl px-6 py-8 md:py-10">
      <nav className="mb-10 flex flex-wrap items-center justify-between gap-4">
        <div>
          <p className="text-xs uppercase tracking-[0.45em] text-rose-200/75">
            Portal da Autora
          </p>
          <h1 className="mt-2 text-2xl font-semibold tracking-tight md:text-3xl">
            A vida por Gabriela Martins
          </h1>
        </div>

        <div className="flex flex-wrap items-center gap-2 text-sm text-[#f5d8cf]">
          {[
            "Início",
            "Livros",
            "Comunidades",
            "Cartas",
            "Teorias",
            "Gabriela Martins",
          ].map((item) => (
            <button
              key={item}
              className="rounded-full border border-white/10 bg-white/5 px-4 py-2 backdrop-blur transition hover:bg-white/10"
            >
              {item}
            </button>
          ))}
        </div>
      </nav>

      <section className="grid items-center gap-8 lg:grid-cols-[1.2fr_0.8fr]">
        <div>
          <div className="inline-flex items-center gap-2 rounded-full border border-[#f7d4bf]/20 bg-[#f7d4bf]/10 px-4 py-2 text-sm text-[#ffd9c4]">
            <Feather className="h-4 w-4" />
            capítulos seriados • cartas • comunidade viva
          </div>

          <h2 className="mt-6 max-w-3xl text-4xl font-semibold leading-tight md:text-6xl">
            Um refúgio para publicar suas histórias e ver seus leitores florescerem junto com elas.
          </h2>

          <p className="mt-5 max-w-2xl text-base leading-8 text-[#e7cfc2] md:text-lg">
            Esta segunda versão tem mais alma de autora romântica e arquiteta de universos. Aqui, cada livro pode ganhar capítulos, comentários, cartas, teorias e pequenos altares de fandom. É menos “site comum” e mais uma casa acesa na madrugada para quem ama histórias com febre, poesia e destino.
          </p>

          <div className="mt-8 flex flex-wrap gap-3">
            <button className="rounded-2xl bg-[#f3c6a8] px-5 py-3 font-medium text-[#2a1718] transition hover:opacity-90">
              Publicar novo capítulo
            </button>
            <button className="rounded-2xl border border-white/10 bg-white/5 px-5 py-3 transition hover:bg-white/10">
              Abrir mural de teorias
            </button>
            <button className="rounded-2xl border border-white/10 bg-white/5 px-5 py-3 transition hover:bg-white/10">
              Ler cartas dos leitores
            </button>
          </div>
        </div>

        <div className="grid gap-4">
          <div className="rounded-[28px] border border-white/10 bg-white/5 p-6 shadow-2xl shadow-black/20 backdrop-blur">
            <div className="flex items-center justify-between gap-3">
              <div>
                <p className="text-sm uppercase tracking-[0.3em] text-[#f0bfa8]/80">
                  Destaque da semana
                </p>
                <h3 className="mt-2 text-2xl font-semibold">Capítulo recém-publicado</h3>
              </div>
              <ScrollText className="h-8 w-8 text-[#f4c9b1]" />
            </div>

            <div className="mt-5 rounded-3xl border border-white/10 bg-[#1a1118] p-5">
              <p className="text-sm text-[#efc9b8]">Entre Marés e Destinos</p>
              <h4 className="mt-2 text-2xl font-semibold">Capítulo 12 • A Árvore que Sonhava</h4>
              <p className="mt-3 leading-7 text-[#e5d3ca]">
                Naquela noite, o vento parecia guardar nomes antigos no bolso, como se a ilha inteira soubesse do reencontro antes deles.
              </p>
              <div className="mt-5 flex flex-wrap gap-3 text-sm">
                <button className="rounded-xl bg-[#f3c6a8] px-4 py-2 font-medium text-[#2a1718]">
                  Continuar leitura
                </button>
                <button className="rounded-xl border border-white/10 bg-white/5 px-4 py-2">
                  128 comentários
                </button>
              </div>
            </div>
          </div>

          <div className="grid gap-4 sm:grid-cols-3">
            {[
              ["14", "capítulos publicados"],
              ["3", "comunidades ativas"],
              ["247", "cartas recebidas"],
            ].map(([value, label]) => (
              <div
                key={label}
                className="rounded-3xl border border-white/10 bg-white/5 p-5 text-center"
              >
                <p className="text-3xl font-semibold text-[#ffd8c6]">{value}</p>
                <p className="mt-2 text-sm text-[#d7beb2]">{label}</p>
              </div>
            ))}
          </div>
        </div>
      </section>
    </div>
  </header>

  <main className="mx-auto max-w-7xl px-6 py-10">
    <section className="grid gap-6 xl:grid-cols-[1.2fr_0.8fr]">
      <div className="rounded-[30px] border border-white/10 bg-white/5 p-6">
        <div className="flex flex-col gap-4 md:flex-row md:items-end md:justify-between">
          <div>
            <p className="text-sm uppercase tracking-[0.3em] text-[#e9b7d0]/80">
              Sua estante viva
            </p>
            <h2 className="mt-2 text-3xl font-semibold">Livros em capítulos</h2>
          </div>

          <label className="flex items-center gap-3 rounded-2xl border border-white/10 bg-[#1b1217] px-4 py-3 text-sm text-[#dcc9c2]">
            <Search className="h-4 w-4" />
            <input
              value={search}
              onChange={(e) => setSearch(e.target.value)}
              placeholder="Buscar por título, gênero ou clima da história"
              className="w-64 bg-transparent outline-none placeholder:text-[#9f8a82]"
            />
          </label>
        </div>

        <div className="mt-6 grid gap-5 md:grid-cols-2">
          {filteredBooks.map((book) => (
            <article
              key={book.title}
              className="rounded-[28px] border border-white/10 bg-[linear-gradient(180deg,_rgba(255,255,255,0.07),_rgba(255,255,255,0.03))] p-5"
            >
              <div className="flex items-start justify-between gap-4">
                <div className="flex items-center gap-4">
                  <div className="flex h-14 w-14 items-center justify-center rounded-2xl bg-[#2b1921] text-2xl shadow-inner shadow-black/30">
                    {book.cover}
                  </div>
                  <div>
                    <h3 className="text-xl font-semibold">{book.title}</h3>
                    <p className="mt-1 text-sm text-[#d1b7ae]">{book.genre}</p>
                  </div>
                </div>
                <span className="rounded-full border border-white/10 bg-white/5 px-3 py-1 text-xs text-[#f5d7cb]">
                  {book.status}
                </span>
              </div>

              <p className="mt-4 leading-7 text-[#e6d3ca]">{book.blurb}</p>

              <div className="mt-5 flex items-center justify-between text-sm text-[#cdb8af]">
                <span>{book.chapters} capítulos</span>
                <button className="rounded-xl border border-white/10 bg-[#20141a] px-4 py-2 text-[#f6ece6] transition hover:bg-[#281922]">
                  Abrir obra
                </button>
              </div>
            </article>
          ))}
        </div>
      </div>

      <div className="space-y-6">
        <div className="rounded-[30px] border border-white/10 bg-white/5 p-6">
          <p className="text-sm uppercase tracking-[0.3em] text-[#f0c39f]/80">
            Menu rápido
          </p>
          <div className="mt-5 space-y-3">
            {[
              { icon: BookOpen, label: "Página de capítulos" },
              { icon: Users, label: "Comunidades por livro" },
              { icon: MessageCircleHeart, label: "Comentários dos leitores" },
              { icon: Mail, label: "Cartas enviadas" },
              { icon: Sparkles, label: "Teorias em destaque" },
              { icon: Heart, label: "Favoritos e trechos salvos" },
            ].map(({ icon: Icon, label }) => (
              <div
                key={label}
                className="flex items-center gap-3 rounded-2xl border border-white/10 bg-[#1a1118] px-4 py-3"
              >
                <Icon className="h-5 w-5 text-[#f4cab3]" />
                <span className="text-sm text-[#eddcd2]">{label}</span>
              </div>
            ))}
          </div>
        </div>

        <div className="rounded-[30px] border border-white/10 bg-[linear-gradient(180deg,_rgba(243,198,168,0.16),_rgba(255,255,255,0.03))] p-6">
          <p className="text-sm uppercase tracking-[0.3em] text-[#ffd6c2]/80">
            Espaço da autora
          </p>
          <h3 className="mt-2 text-2xl font-semibold">Recados, bastidores e promessas perigosas</h3>
          <p className="mt-4 leading-7 text-[#f0dfd7]">
            Este bloco pode virar seu canto pessoal: notas sobre o processo de escrita, playlists, estética dos personagens, cronograma de postagens e avisos para as leitoras que vivem farejando spoiler no ar.
          </p>
          <button className="mt-5 rounded-2xl bg-[#f3c6a8] px-4 py-3 font-medium text-[#2a1718]">
            Editar recado da semana
          </button>
        </div>
      </div>
    </section>

    <section className="mt-10 grid gap-6 xl:grid-cols-[1fr_1fr_0.9fr]">
      <div className="rounded-[30px] border border-white/10 bg-white/5 p-6">
        <p className="text-sm uppercase tracking-[0.3em] text-[#b8d5ff]/80">
          Últimos capítulos
        </p>
        <div className="mt-5 space-y-4">
          {latestChapters.map((item) => (
            <article
              key={item.chapter}
              className="rounded-2xl border border-white/10 bg-[#1a1118] p-4"
            >
              <p className="text-xs uppercase tracking-[0.25em] text-[#99857b]">{item.book}</p>
              <h3 className="mt-2 text-lg font-medium">{item.chapter}</h3>
              <p className="mt-1 text-sm text-[#c5b1a8]">Publicado em {item.date}</p>
              <p className="mt-3 text-sm leading-7 text-[#e7d6ce]">{item.excerpt}</p>
            </article>
          ))}
        </div>
      </div>

      <div className="rounded-[30px] border border-white/10 bg-white/5 p-6">
        <p className="text-sm uppercase tracking-[0.3em] text-[#c6f0cf]/80">
          Comunidades
        </p>
        <div className="mt-5 space-y-4">
          {communities.map((community) => {
            const Icon = community.icon;
            return (
              <article
                key={community.title}
                className="rounded-2xl border border-white/10 bg-[#1a1118] p-4"
              >
                <div className="flex items-start justify-between gap-4">
                  <div className="flex items-center gap-3">
                    <div className="rounded-2xl bg-[#2a1820] p-3">
                      <Icon className="h-5 w-5 text-[#f3c6a8]" />
                    </div>
                    <div>
                      <h3 className="text-lg font-medium">{community.title}</h3>
                      <p className="text-sm text-[#cdb8ae]">{community.members}</p>
                    </div>
                  </div>
                </div>
                <p className="mt-4 text-sm leading-7 text-[#e5d5cd]">{community.desc}</p>
                <button className="mt-4 rounded-xl border border-white/10 bg-white/5 px-4 py-2 text-sm transition hover:bg-white/10">
                  Entrar na comunidade
                </button>
              </article>
            );
          })}
        </div>
      </div>

      <div className="rounded-[30px] border border-white/10 bg-white/5 p-6">
        <p className="text-sm uppercase tracking-[0.3em] text-[#f2d39a]/80">
          Teorias em alta
        </p>
        <div className="mt-5 space-y-3">
          {theories.map((theory, index) => (
            <div
              key={theory}
              className="rounded-2xl border border-white/10 bg-[#1a1118] p-4"
            >
              <p className="text-xs uppercase tracking-[0.25em] text-[#9d897f]">
                teoria {index + 1}
              </p>
              <p className="mt-2 text-sm leading-7 text-[#f0e2db]">{theory}</p>
            </div>
          ))}
        </div>
        <button className="mt-5 w-full rounded-2xl bg-[#efb7d1] px-4 py-3 font-medium text-[#301821] transition hover:opacity-90">
          Abrir mural completo
        </button>
      </div>
    </section>

    <section className="mt-10 grid gap-6 lg:grid-cols-[1.15fr_0.85fr]">
      <div className="rounded-[30px] border border-white/10 bg-white/5 p-6">
        <div className="flex items-end justify-between gap-4">
          <div>
            <p className="text-sm uppercase tracking-[0.3em] text-[#f5b9b9]/80">
              Cartas dos leitores
            </p>
            <h2 className="mt-2 text-3xl font-semibold">Mensagens que chegam feito vento em cortina</h2>
          </div>
          <button className="rounded-2xl border border-white/10 bg-white/5 px-4 py-2 text-sm transition hover:bg-white/10">
            Escrever carta
          </button>
        </div>

        <div className="mt-6 grid gap-4 md:grid-cols-2">
          {highlightedLetters.map((letter) => (
            <article
              key={letter.title}
              className="rounded-[28px] border border-white/10 bg-[#1a1118] p-5"
            >
              <p className="text-sm uppercase tracking-[0.25em] text-[#c6b3ab]">{letter.title}</p>
              <p className="mt-2 text-sm text-[#efc8b4]">{letter.author}</p>
              <p className="mt-4 leading-7 text-[#efe1d9]">“{letter.text}”</p>
            </article>
          ))}
        </div>
      </div>

      <div className="rounded-[30px] border border-white/10 bg-[radial-gradient(circle_at_top,_rgba(239,183,209,0.18),_transparent_28%),linear-gradient(180deg,_rgba(255,255,255,0.06),_rgba(255,255,255,0.03))] p-6">
        <p className="text-sm uppercase tracking-[0.3em] text-[#f4cbdb]/85">
          Sobre a autora
        </p>
        <h2 className="mt-2 text-3xl font-semibold">A vida contada em capítulos por Gabriela Martins</h2>
        <p className="mt-4 leading-8 text-[#f2e1db]">
          Aqui pode entrar sua apresentação oficial: quem você é, o que escreve, seus universos favoritos, sua estética e a forma como convida leitores a caminhar com você capítulo por capítulo. Um lugar para sua voz respirar fora da ficção, mas ainda coberta de encanto.
        </p>

        <div className="mt-6 space-y-3">
          {[
            "Romances por capítulos",
            "Fantasia cinematográfica",
            "Comunidade de leitoras apaixonadas",
            "Espaço para teorias e cartas",
          ].map((item) => (
            <div
              key={item}
              className="rounded-2xl border border-white/10 bg-[#1a1118] px-4 py-3 text-sm text-[#f2dfd8]"
            >
              {item}
            </div>
          ))}
        </div>
      </div>
    </section>
  </main>
</div>

); }