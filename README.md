# App Router — Next.js Learn Dashboard

Repositório de estudos acompanhando o curso oficial [**Next.js Learn — App Router**](https://nextjs.org/learn/dashboard-app) (o projeto **Acme Dashboard**, da Vercel).

Cada capítulo é uma **cópia independente** do projeto que continua de onde o anterior parou, permitindo voltar e comparar o código em qualquer etapa do curso.

## 📚 Capítulos

| # | Pasta | Tema | Status |
|---|-------|------|:------:|
| 1 | `Chapter 1 Getting Started` | Configuração inicial do projeto | ✅ |
| 2 | `Chapter 2 CSS Styling` | Estilização com Tailwind e CSS Modules | ✅ |
| 3 | `Chapter 3 Optimizing Fonts and Images` | Otimização de fontes (`next/font`) e imagens (`next/image`) | ✅ |
| 4 | `Chapter 4 Creating Layouts and Pages` | Layouts, páginas e rotas aninhadas | ✅ |
| 5 | `Chapter 5 Navigating Between Pages` | Navegação com `<Link>` e prefetching | ⬜ |
| 6 | `Chapter 6 Setting Up Your Database` | Configuração do banco de dados (Postgres) | ⬜ |
| 7 | `Chapter 7 Fetching Data` | Busca de dados com Server Components | ⬜ |
| 8 | `Chapter 8 Static and Dynamic Rendering` | Renderização estática vs. dinâmica | ⬜ |
| 9 | `Chapter 9 Streaming` | Streaming com `loading.tsx` e `<Suspense>` | ⬜ |
| 10 | `Chapter 10 Partial Prerendering` | Partial Prerendering (PPR) | ⬜ |
| 11 | `Chapter 11 Adding Search and Pagination` | Busca e paginação com URL search params | ⬜ |
| 12 | `Chapter 12 Mutating Data` | Mutação de dados com Server Actions | ⬜ |
| 13 | `Chapter 13 Handling Errors` | Tratamento de erros (`error.tsx`, `not-found.tsx`) | ⬜ |
| 14 | `Chapter 14 Improving Accessibility` | Acessibilidade e validação de formulários | ⬜ |
| 15 | `Chapter 15 Adding Authentication` | Autenticação com NextAuth.js | ⬜ |
| 16 | `Chapter 16 Adding Metadata` | Metadados e SEO | ⬜ |

Cada pasta contém o projeto completo em `nextjs-dashboard/`. Marque o **Status** como ✅ conforme concluir cada capítulo.

## 🛠️ Stack

- **[Next.js](https://nextjs.org) 16** (App Router + Turbopack)
- **React 19** · **TypeScript 5.7**
- **Tailwind CSS 3.4**
- **NextAuth 5 (beta)** · **postgres** · **Zod** · **bcrypt**
- Gerenciador de pacotes: **pnpm**

## ✅ Pré-requisitos

- [Node.js](https://nodejs.org) 20+ (testado com v24)
- [pnpm](https://pnpm.io) 11+ (`npm install -g pnpm`)

## 🚀 Como rodar um capítulo

A partir da raiz do repositório, escolha o capítulo desejado:

```powershell
# Instalar dependências
pnpm -C "Chapter 4 Creating Layouts and Pages/nextjs-dashboard" install

# Rodar o servidor de desenvolvimento
pnpm -C "Chapter 4 Creating Layouts and Pages/nextjs-dashboard" dev
```

Depois abra **http://localhost:3000**. Para parar o servidor: `Ctrl+C`.

> Também é possível entrar na pasta (`cd "Chapter 4 .../nextjs-dashboard"`) e rodar `pnpm install` / `pnpm dev` diretamente.

## 📜 Scripts disponíveis (por capítulo)

| Script | Ação |
|--------|------|
| `pnpm dev` | Servidor de desenvolvimento (`next dev --turbopack`) |
| `pnpm build` | Build de produção |
| `pnpm start` | Servir o build de produção |

## ⚠️ Notas de configuração

- **Build scripts nativos:** `bcrypt` e `sharp` precisam compilar binários. No pnpm 10+ isso é aprovado via `onlyBuiltDependencies` no `pnpm-workspace.yaml` de cada projeto. Se o `pnpm install` falhar com `ERR_PNPM_IGNORED_BUILDS`, rode `pnpm approve-builds --all`.
- **Variáveis de ambiente:** copie `.env.example` para `.env` e preencha as credenciais do banco (a partir do Capítulo 6).

## 🔗 Referências

- [Next.js Learn Course](https://nextjs.org/learn/dashboard-app)
- [Documentação do Next.js](https://nextjs.org/docs)
