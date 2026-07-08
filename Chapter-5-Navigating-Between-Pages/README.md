# Capítulo 5 — Navigating Between Pages

Navegação **client-side** com o componente `<Link>` e destaque do link ativo com `usePathname()`.

## 🎯 O que se aprende

- Trocar `<a>` por `<Link>` para navegar sem recarregar a página
- Como o Next faz _code-splitting_ e _prefetching_ automáticos
- Destacar o link ativo com o hook `usePathname()`

## 🔗 `<Link>` no lugar de `<a>`

Com `<a>`, cada clique recarrega a página inteira. Com `<Link>`, a navegação é **client-side** (sem reload) e mais rápida:

```tsx
import Link from 'next/link';

// ❌ Recarrega a página toda
<a href="/dashboard">Dashboard</a>

// ✅ Navegação instantânea (client-side)
<Link href="/dashboard">Dashboard</Link>
```

**Automático com `<Link>`:**
- **Code-splitting:** cada rota carrega só o código que precisa.
- **Prefetching:** no viewport, o Next pré-carrega a rota em background — o clique fica instantâneo.

## 🎯 Destacando o link ativo com `usePathname()`

O `usePathname()` retorna a URL atual. Combinado com `clsx`, dá pra estilizar o link da página em que você está. Como é um hook, o componente precisa ser **Client Component** (`'use client'`):

```tsx
// app/ui/dashboard/nav-links.tsx
'use client';

import Link from 'next/link';
import { usePathname } from 'next/navigation';
import clsx from 'clsx';

export default function NavLinks() {
  const pathname = usePathname();

  return (
    <>
      {links.map((link) => (
        <Link
          key={link.name}
          href={link.href}
          className={clsx(
            'flex items-center gap-2 rounded-md p-3 hover:bg-sky-100 hover:text-blue-600',
            {
              // aplicado só quando a rota bate com o link
              'bg-sky-100 text-blue-600': pathname === link.href,
            },
          )}
        >
          {link.name}
        </Link>
      ))}
    </>
  );
}
```

## 🧠 Server vs Client Components

- Por padrão, componentes no App Router são **Server Components**.
- Hooks como `usePathname()`, `useState`, `useEffect` exigem `'use client'` no topo do arquivo.

## 📖 Referência

[Next.js Learn — Chapter 5](https://nextjs.org/learn/dashboard-app/navigating-between-pages)
