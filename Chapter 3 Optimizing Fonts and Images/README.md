# Capítulo 3 — Optimizing Fonts and Images

Otimização de **fontes** (`next/font`) e **imagens** (`next/image`) — dois recursos que melhoram performance e evitam _layout shift_.

## 🎯 O que se aprende

- Carregar fontes do Google de forma otimizada (sem _layout shift_)
- Aplicar fontes via `className`
- Usar o componente `<Image>` para otimização automática

## 🔤 Fontes com `next/font/google`

As fontes são baixadas em **build time** e auto-hospedadas — nenhum request extra ao Google e **zero layout shift** (CLS).

```ts
// app/ui/fonts.ts
import { Inter, Lusitana } from 'next/font/google';

export const inter = Inter({ subsets: ['latin'] });

export const lusitana = Lusitana({
  weight: ['400', '700'],
  subsets: ['latin'],
});
```

Aplicando a fonte principal no `<body>`:

```tsx
// app/layout.tsx
import { inter } from '@/app/ui/fonts';

<body className={`${inter.className} antialiased`}>{children}</body>
```

E uma fonte secundária em elementos específicos:

```tsx
import { lusitana } from '@/app/ui/fonts';

<p className={`${lusitana.className} text-xl`}>Welcome to Acme.</p>
```

## 🖼️ Imagens com `next/image`

O `<Image>` faz otimização automática: **lazy loading**, formatos modernos (WebP/AVIF) e reserva de espaço para **evitar CLS**.

```tsx
import Image from 'next/image';

<Image
  src="/hero-desktop.png"
  width={1000}   // largura/altura reais → evita layout shift
  height={760}
  className="hidden md:block"   // só aparece no desktop
  alt="Screenshots do dashboard (versão desktop)"
/>
<Image
  src="/hero-mobile.png"
  width={560}
  height={620}
  className="block md:hidden"   // só aparece no mobile
  alt="Screenshot do dashboard (versão mobile)"
/>
```

**Boas práticas:**
- Sempre defina `width` e `height` (ou use `fill`) para reservar o espaço.
- Sempre inclua `alt` (acessibilidade + SEO).
- Use classes responsivas para trocar a imagem entre desktop e mobile.

## 📖 Referência

[Next.js Learn — Chapter 3](https://nextjs.org/learn/dashboard-app/optimizing-fonts-images)
