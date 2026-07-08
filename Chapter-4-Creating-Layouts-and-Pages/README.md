# Capítulo 4 — Creating Layouts and Pages

Criação de **rotas aninhadas** e **layouts compartilhados** usando o roteamento por sistema de arquivos do App Router.

## 🎯 O que se aprende

- Como o Next cria rotas a partir de pastas
- Diferença entre `page.tsx` e `layout.tsx`
- Layouts compartilhados e _partial rendering_

## 🗂️ Roteamento por pastas

Cada pasta em `app/` é um segmento de URL; o `page.tsx` torna a rota **acessível**:

```
app/
├── page.tsx                    →  /
└── dashboard/
    ├── page.tsx                →  /dashboard
    ├── customers/page.tsx      →  /dashboard/customers
    └── invoices/page.tsx       →  /dashboard/invoices
```

Um `page.tsx` simples:

```tsx
// app/dashboard/page.tsx
export default function Page() {
  return <p>Dashboard Page</p>;
}
```

## 🧩 Layouts compartilhados

Um `layout.tsx` envolve todas as páginas **abaixo** dele. Aqui a `<SideNav />` fica fixa enquanto só o conteúdo (`children`) troca:

```tsx
// app/dashboard/layout.tsx
import SideNav from '@/app/ui/dashboard/sidenav';

export default function Layout({ children }: { children: React.ReactNode }) {
  return (
    <div className="flex h-screen flex-col md:flex-row md:overflow-hidden">
      <div className="w-full flex-none md:w-64">
        <SideNav />
      </div>
      <div className="flex-grow p-6 md:overflow-y-auto md:p-12">{children}</div>
    </div>
  );
}
```

**Partial rendering:** ao navegar entre `/dashboard/customers` e `/dashboard/invoices`, o layout (a `<SideNav />`) **não é re-renderizado** — só o `children` muda. Isso preserva estado e melhora a performance.

## 🌳 Hierarquia de layouts

```
RootLayout (app/layout.tsx)
   └── DashboardLayout (app/dashboard/layout.tsx)
          └── page.tsx da rota atual
```

O layout raiz define `<html>` e `<body>`; layouts mais internos adicionam UI específica da seção.

## 📖 Referência

[Next.js Learn — Chapter 4](https://nextjs.org/learn/dashboard-app/creating-layouts-and-pages)
