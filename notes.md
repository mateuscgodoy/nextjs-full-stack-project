# Notes from Videos

> <br>✍️ On this document you can find some of the notes I've highlighted from Davids lectures, composed of all information that was new or remarkable.<br><br>

## Lecture 01

shadcn is an open-source component library that allow developers to install individual base components for their applications, like a `button`.

---

Tailwind-CSS allow images to be registered, like so:

```ts
import type { Config } from 'tailwindcss';

export default {
  // (...)
  theme: {
    extend: {
      backgroundImage: {
        'home-img': "url('/images/home-img.jpg')",
      },
      // (...)
    },
  },
  // (...)
} satisfies Config;
```

Then, inside a certain page this background image can be used like so: `bg-home-img`. This is **important** the named registered was `home-img`, but to use it a `bg-` must be added, for example:
```jsx
<div className="bg-black bg-home-img">
      
</div>
```

---

Difference between `layout.tsx` and `template.tsx` in Nextjs is that the **`layout` only loads once**, when the application first loads, while the **`template` is loaded multiple times** as users navigate.

---

The reusable component for `NavButton.tsx` was very elegant, it can be reused easily since it does not assume any sort of hard-coded information.

---

`tailwind.config.ts` can also be used to define animations using the following syntax:

```ts
import type { Config } from 'tailwindcss';

export default {
  darkMode: ['class'],
  content: [
   // (...)
  ],
  theme: {
    extend: {
      backgroundImage: {
       
      },
      colors: {
       // (...)
      },
      borderRadius: {
      // (...)
      },
      keyframes: {
        appear: {
          from: {
            opacity: '0',
          },
          to: {
            opacity: '1',
          },
        },
        slide: {
          from: {
            transform: 'translateX(100%)',
          },
          to: {
            transform: 'translateX(0%)',
          },
        },
      },
      animation: {
        appear: 'appear 1s ease-in-out',
        slide: 'slide 750ms ease-in-out',
      },
    },
  },
  plugins: [require('tailwindcss-animate')],
} satisfies Config;
```

It creates 2 animations `slide` and `appear` by first defining their `to` and `from` `keyframes: {...}` and then setting the command that will allow their usage, inside `animation: {...}`.

On top of that these 2 animations highlight the difference between `layout` and `template`, the animation `appear` is being used by the `template` therefor it triggers on every navigation, while the `slide` is only used on the `layout`, which only triggers once!

---

Installed shadcn Dark Mode using: `npm install next-themes` (only works for Nextjs), and followed all the instructions as described: [Shadcn Docs Dark Mode](https://ui.shadcn.com/docs/dark-mode/next).

---