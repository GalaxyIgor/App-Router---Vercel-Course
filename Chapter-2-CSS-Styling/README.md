# Capítulo 2 — CSS Styling

Como estilizar a aplicação usando **Tailwind CSS**, **CSS Modules** e a biblioteca **clsx**.

## 🎯 O que se aprende

- Adicionar estilos globais com Tailwind
- Usar classes utilitárias do Tailwind
- Alternativa com **CSS Modules**
- Aplicar classes condicionais com **clsx**

## 🌐 Estilos globais + Tailwind

O `app/ui/global.css` importa as camadas do Tailwind e é carregado **uma vez** no layout raiz:

```css
/* app/ui/global.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

```tsx
// app/layout.tsx
import '@/app/ui/global.css';
```

> Importar CSS global só é permitido no layout raiz — vale para toda a app.

## 🎨 Classes utilitárias do Tailwind

Em vez de escrever CSS, você compõe estilos direto no JSX:

```tsx
<h1 className="text-xl text-gray-800 md:text-3xl">Olá</h1>
//            └ tamanho  └ cor       └ responsivo (a partir de md)
```

## 🧩 CSS Modules (alternativa)

Arquivos `*.module.css` geram classes com escopo local (sem conflito de nomes):

```css
/* app/ui/home.module.css */
.shape {
  height: 0;
  width: 0;
  border-bottom: 30px solid black;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}
```

```tsx
import styles from '@/app/ui/home.module.css';

<div className={styles.shape} />
```

## 🔀 Classes condicionais com clsx

`clsx` liga/desliga classes conforme uma condição — ótimo para estados:

```tsx
import clsx from 'clsx';

<span
  className={clsx('rounded-full px-2 py-1', {
    'bg-gray-100 text-gray-500': status === 'pending',
    'bg-green-500 text-white': status === 'paid',
  })}
>
  {status}
</span>
```

## 📖 Referência

[Next.js Learn — Chapter 2](https://nextjs.org/learn/dashboard-app/css-styling)
