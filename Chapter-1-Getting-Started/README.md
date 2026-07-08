# Capítulo 1 — Getting Started

Configuração inicial do projeto e primeiro contato com a estrutura de um app Next.js (App Router).

## 🎯 O que se aprende

- Criar um projeto Next.js a partir do exemplo do curso
- Entender a **estrutura de pastas** do App Router
- Rodar o servidor de desenvolvimento

## 📂 Estrutura de pastas

```
nextjs-dashboard/
├── app/            # Rotas, componentes e lógica (o coração do App Router)
│   ├── lib/        # Funções utilitárias e dados (ex.: placeholder-data)
│   ├── ui/         # Componentes de interface (botões, cards, etc.)
│   ├── layout.tsx  # Layout raiz (envolve TODAS as páginas)
│   └── page.tsx    # Página inicial (rota "/")
├── public/         # Arquivos estáticos (imagens, fontes)
├── next.config.ts  # Configuração do Next.js
└── package.json    # Dependências e scripts
```

**Conceito-chave:** no App Router, **cada pasta dentro de `app/` vira uma rota**, e o arquivo `page.tsx` define a UI daquela rota.

## 🧩 O layout raiz

O `app/layout.tsx` é obrigatório — ele envolve toda a aplicação:

```tsx
export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  );
}
```

`{children}` é onde cada página é renderizada dentro do layout.

## ▶️ Rodando o projeto

```powershell
pnpm install   # instala as dependências
pnpm dev       # sobe o servidor em http://localhost:3000
```

> ⚠️ Se aparecer `ERR_PNPM_IGNORED_BUILDS` (bcrypt/sharp), rode `pnpm approve-builds --all`.

## 📖 Referência

[Next.js Learn — Chapter 1](https://nextjs.org/learn/dashboard-app/getting-started)
