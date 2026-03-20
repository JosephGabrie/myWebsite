<script lang="ts">
  import { spring } from "svelte/motion";

  const c1 = spring({ x: -100, y: -100 }, { stiffness: 0.05, damping: 0.3 });
  const c2 = spring({ x: -100, y: -100 }, { stiffness: 0.03, damping: 0.4 });
  const c3 = spring({ x: -100, y: -100 }, { stiffness: 0.07, damping: 0.5 });

  let a1 = 0;
  let a2 = 0;
  let a3 = 0;

  let fishWrapper: HTMLElement;

  function handleMousemove(e: MouseEvent) {
    if (!fishWrapper) return;
    const rect = fishWrapper.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const y = e.clientY - rect.top;

    a1 = Math.atan2(y - $c1.y, x - $c1.x) * (180 / Math.PI);
    a2 = Math.atan2(y + 20 - $c2.y, x - 40 - $c2.x) * (180 / Math.PI);
    a3 = Math.atan2(y - 30 - $c3.y, x + 20 - $c3.x) * (180 / Math.PI);

    // Set target positions with slight offsets so they form a "school"
    c1.set({ x, y });
    c2.set({ x: x - 40, y: y + 20 });
    c3.set({ x: x + 20, y: y - 30 });
  }
</script>

<svelte:window onmousemove={handleMousemove} />

<div class="relative w-full">
  <div class="flex h-[50vh] items-center justify-center bg-gray-100 text-black">
    hello
  </div>
  <div
    class="relative flex h-[50vh] items-center justify-center bg-gradient-to-t from-blue-800 to-blue-300 text-white"
  >
    <div
      class="pointer-events-none absolute left-0 top-0 w-full -translate-y-[calc(100%-1px)] transform overflow-hidden leading-none"
    >
      <svg
        class="wave-svg h-16 w-[200%] text-blue-300"
        viewBox="0 0 2400 120"
        preserveAspectRatio="none"
        fill="currentColor"
      >
        <path
          d="M0,60 Q300,120 600,60 T1200,60 T1800,60 T2400,60 L2400,120 L0,120 Z"
        />
      </svg>
    </div>
    bye
  </div>

  <div
    class="absolute left-1/2 top-1/2 z-30 flex h-[60vh] w-[85vw] max-w-4xl -translate-x-1/2 -translate-y-1/2 flex-col overflow-hidden rounded-xl bg-[#FAFAFA] shadow-2xl ring-1 ring-black/5 md:w-[70vw]"
  >
    <!-- Top Bar -->
    <div
      class="flex h-10 w-full items-center bg-[#444] px-4 font-mono text-sm text-gray-300 shadow-sm"
    >
      home
    </div>

    <!-- Content -->
    <div
      class="flex flex-1 flex-col items-center justify-center p-8 text-[#333]"
    >
      <h1
        class="text-center font-sans text-6xl font-medium tracking-tight md:text-8xl"
      >
        Hi! <span class="font-medium text-amber-500">i'm Joseph</span>
      </h1>

      <p class="mt-4 text-center font-sans text-xl text-gray-500 md:text-2xl">
        Fullstack and Game Developer
      </p>

      <!-- Icons Row -->
      <div class="mt-16 flex flex-wrap justify-center gap-8 md:gap-12">
        <a
          href="#about"
          class="group flex flex-col items-center gap-3 transition-transform hover:-translate-y-1"
        >
          <svg
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="1.5"
            stroke-linecap="round"
            stroke-linejoin="round"
            class="h-14 w-14 text-[#333] drop-shadow-[3px_4px_0_#d1d5db]"
          >
            <path
              d="M21 11.5a8.38 8.38 0 0 1-.9 3.8 8.5 8.5 0 0 1-7.6 4.7 8.38 8.38 0 0 1-3.8-.9L3 21l1.9-5.7a8.38 8.38 0 0 1-.9-3.8 8.5 8.5 0 0 1 4.7-7.6 8.38 8.38 0 0 1 3.8-.9h.5a8.48 8.48 0 0 1 8 8v.5z"
            />
            <line x1="12" y1="16" x2="12" y2="12" />
            <line x1="12" y1="8" x2="12.01" y2="8" />
          </svg>
          <span class="font-mono text-sm font-bold tracking-widest text-[#333]"
            >about</span
          >
        </a>

        <a
          href="#work"
          class="group flex flex-col items-center gap-3 transition-transform hover:-translate-y-1"
        >
          <svg
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="1.5"
            stroke-linecap="round"
            stroke-linejoin="round"
            class="h-14 w-14 text-[#333] drop-shadow-[3px_4px_0_#d1d5db]"
          >
            <path
              d="M4 20h16a2 2 0 0 0 2-2V8a2 2 0 0 0-2-2h-7.9a2 2 0 0 1-1.69-.9L9.6 3.9A2 2 0 0 0 7.93 3H4a2 2 0 0 0-2 2v13c0 1.1.9 2 2 2Z"
            />
            <path d="M8 10h8v10H8z" />
          </svg>
          <span class="font-mono text-sm font-bold tracking-widest text-[#333]"
            >work</span
          >
        </a>

        <a
          href="https://x.com/JosephNgabrie"
          target="_blank"
          rel="noopener noreferrer"
          class="group flex flex-col items-center gap-3 transition-transform hover:-translate-y-1"
        >
          <svg
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="1.5"
            stroke-linecap="round"
            stroke-linejoin="round"
            class="h-14 w-14 text-[#333] drop-shadow-[3px_4px_0_#d1d5db]"
          >
            <polygon points="4 4 10 4 20 20 14 20" fill="transparent" />
            <line x1="20" y1="4" x2="4" y2="20" />
          </svg>
          <span class="font-mono text-sm font-bold tracking-widest text-[#333]"
            >x</span
          >
        </a>

        <a
          href="https://github.com/JosephGabrie"
          target="_blank"
          rel="noopener noreferrer"
          class="group flex flex-col items-center gap-3 transition-transform hover:-translate-y-1"
        >
          <svg
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="1.5"
            stroke-linecap="round"
            stroke-linejoin="round"
            class="h-14 w-14 text-[#333] drop-shadow-[3px_4px_0_#d1d5db]"
          >
            <path
              d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"
            ></path>
          </svg>
          <span class="font-mono text-sm font-bold tracking-widest text-[#333]"
            >github</span
          >
        </a>

        <a
          href="https://www.youtube.com/@JosephNGabrie"
          target="_blank"
          rel="noopener noreferrer"
          class="group flex flex-col items-center gap-3 transition-transform hover:-translate-y-1"
        >
          <svg
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="1.5"
            stroke-linecap="round"
            stroke-linejoin="round"
            class="h-14 w-14 text-[#333] drop-shadow-[3px_4px_0_#d1d5db]"
          >
            <path
              d="M22.54 6.42a2.78 2.78 0 0 0-1.94-2C18.88 4 12 4 12 4s-6.88 0-8.6.46a2.78 2.78 0 0 0-1.94 2A29 29 0 0 0 1 11.75a29 29 0 0 0 .46 5.33A2.78 2.78 0 0 0 3.4 19c1.72.46 8.6.46 8.6.46s6.88 0 8.6-.46a2.78 2.78 0 0 0 1.94-2 29 29 0 0 0 .46-5.25 29 29 0 0 0-.46-5.33z"
            ></path>
            <polygon points="9.75 15.02 15.5 11.75 9.75 8.48 9.75 15.02"
            ></polygon>
          </svg>
          <span class="font-mono text-sm font-bold tracking-widest text-[#333]"
            >youtube</span
          >
        </a>
      </div>
    </div>
  </div>
</div>
<div
  class="relative flex min-h-screen w-full flex-col items-center justify-center overflow-hidden bg-gradient-to-t from-black to-blue-800 py-20 text-white"
>
  <!-- Left Coral -->
  <div
    class="pointer-events-none absolute left-0 top-1/2 -translate-y-1/2 z-10 hidden md:block opacity-60"
  >
    <svg
      width="250"
      height="200"
      viewBox="0 0 250 200"
      xmlns="http://www.w3.org/2000/svg"
      class="-scale-y-100"
    >
      <path
        d="M0,20 Q70,10 130,20 T200,40 T230,60 Q180,50 110,40 T0,60"
        fill="#fb7185"
        opacity="0.8"
      />
      <path
        d="M0,60 Q30,80 90,100 T180,130 T220,160 Q150,140 80,110 T0,120"
        fill="#f43f5e"
        opacity="0.7"
      />
      <path
        d="M0,120 Q40,140 80,170 T150,230 T180,250 Q120,200 60,170 T0,180"
        fill="#fb923c"
        opacity="0.6"
      />
    </svg>
  </div>
  <!-- Right Coral -->
  <div
    class="pointer-events-none absolute right-0 top-1/2 -translate-y-1/2 z-10 hidden md:block opacity-60"
  >
    <svg
      width="250"
      height="200"
      viewBox="0 0 250 200"
      xmlns="http://www.w3.org/2000/svg"
      class="-scale-y-100"
    >
      <path
        d="M250,20 Q180,10 120,20 T50,40 T20,60 Q70,50 140,40 T250,60"
        fill="#ec4899"
        opacity="0.8"
      />
      <path
        d="M250,60 Q220,80 160,100 T70,130 T30,160 Q100,140 170,110 T250,120"
        fill="#d946ef"
        opacity="0.7"
      />
      <path
        d="M250,120 Q210,140 170,170 T100,230 T70,250 Q130,200 190,170 T250,180"
        fill="#8b5cf6"
        opacity="0.6"
      />
    </svg>
  </div>

  <div
    class="relative z-30 flex w-[85vw] max-w-4xl flex-col overflow-hidden rounded-xl bg-[#15202B] text-slate-100 shadow-2xl ring-1 ring-white/10 md:w-[70vw]"
  >
    <!-- Top Window Bar -->
    <div
      class="flex h-10 w-full shrink-0 items-center justify-between border-b border-white/5 bg-[#1e293b] px-4 font-mono text-sm text-slate-300 shadow-sm"
    >
      <section id="about">
        <span>about</span>
      </section>
    </div>

    <div class="flex max-h-[80vh] flex-col overflow-y-auto p-8 md:p-12">
      <!-- Header row -->
      <div class="flex flex-col gap-6 md:flex-row md:items-center md:gap-8">
        <!-- Profile image -->
        <div
          class="flex h-28 w-28 shrink-0 items-center justify-center overflow-hidden rounded-full border-4 border-slate-700 bg-teal-900 shadow-inner md:h-32 md:w-32"
        >
          <span class="font-mono text-xs text-teal-200/50">(profile)</span>
        </div>
        <!-- Title & Subtitle -->
        <div class="flex flex-col">
          <h2
            class="font-sans text-4xl font-medium tracking-tight text-cyan-200 md:text-5xl"
          >
            Joseph Gabrie <span
              class="font-sans text-2xl font-light tracking-normal opacity-80 text-cyan-200/80"
            ></span>
          </h2>
          <p class="mt-2 text-slate-300">
            Full stack develop using AI to make apps into reality<br />
            Former web developer at
            <a
              href="https://apex-software.dev/"
              class="text-cyan-200 hover:underline">Apex software</a
            >
          </p>
        </div>
      </div>
      <!-- Body -->
      <div
        class="mt-10 max-w-3xl font-sans text-lg leading-relaxed text-slate-300"
      >
        <p>Hi! i'm Joseph, a game and web developer. i...</p>
        <ul class="mt-4 list-disc space-y-2 pl-6 marker:text-slate-500">
          <li>
            create <a href="/" class="text-cyan-200 hover:underline"
              >hand-drawn animations</a
            >,
          </li>
          <li>
            create <a href="/" class="text-cyan-200 hover:underline">videos</a> talking
            about things i like,
          </li>
          <li>create website wireframes, and</li>
          <li>do frontend web development!</li>
        </ul>
        <p class="mt-8 font-medium">
          interested in working with me? send me an email at <a
            href="mailto:josephgabriemolina@gmail.com"
            class="text-cyan-200 hover:underline"
            >josephgabriemolina@gmail.com</a
          >
        </p>
      </div>

      <!-- Language Proficiency Header -->
      <h3
        class="mt-16 font-mono text-xl font-bold tracking-widest text-[#E2E8F0] uppercase"
      >
        LANGUAGE PROFICIENCY
      </h3>
      <div
        class="mt-6 border-l-[3px] border-slate-300 pl-6 flex flex-col gap-4 max-w-2xl"
      >
        <p class="font-sans text-lg leading-relaxed text-slate-200">
          i have native fluency in <span class="text-cyan-200">English</span>
          and
          <span class="text-cyan-200">Spanish</span>
        </p>
        <p class="font-sans text-sm leading-relaxed text-slate-400">
          i speak a little bit of Japanese and russian, but at a very pre-school
          proficiency!
        </p>
      </div>
    </div>
  </div>
</div>

<div class="relative w-full z-20" style="height: 0;">
  <div
    class="fish-container absolute -top-32 left-0 flex h-64 w-64 items-center justify-center rounded-full bg-transparent text-white"
  >
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="128"
      height="128"
      viewBox="0 0 24 24"
      fill="none"
      stroke="currentColor"
      stroke-width="1"
      stroke-linecap="round"
      stroke-linejoin="round"
      class="overflow-visible"
    >
      <defs>
        <filter id="lure-glow" x="-500%" y="-500%" width="1000%" height="1000%">
          <feGaussianBlur stdDeviation="6" result="blur" />
        </filter>
      </defs>
      <path d="M6 12c0-4 4-6 8-6 4 0 6 3 6 6s-2 6-6 6c-4 0-8-2-8-6" />
      <path d="M6 12L2 9v6L6 12z" fill="currentColor" stroke="none" />
      <circle cx="15" cy="10" r="1" fill="currentColor" />
      <path d="M20 12l-2 1-1-1-1 1-1-1-1 1" />
      <path d="M12 6c0-3 3-4 5-4s4 1 5 3" />
      <circle
        cx="22"
        cy="5"
        r="8"
        fill="rgba(255,255,255,0.7)"
        filter="url(#lure-glow)"
        stroke="none"
      />
      <circle cx="22" cy="5" r="2" fill="currentColor" stroke="none" />
    </svg>
  </div>
</div>

<div
  class="relative flex min-h-screen w-full flex-col items-center justify-center overflow-hidden bg-black py-20"
>
  <!-- Left Plankton -->
  <div
    class="pointer-events-none absolute inset-y-0 left-0 z-10 hidden md:flex items-center"
  >
    <svg
      width="150"
      height="600"
      viewBox="0 0 150 600"
      xmlns="http://www.w3.org/2000/svg"
    >
      <circle cx="40" cy="100" r="3" fill="#ffffff" opacity="0.4"
        ><animate
          attributeName="opacity"
          values="0.1;0.6;0.1"
          dur="4s"
          repeatCount="indefinite"
        /></circle
      >
      <circle cx="110" cy="250" r="2" fill="#ffffff" opacity="0.6"
        ><animate
          attributeName="opacity"
          values="0.2;0.8;0.2"
          dur="5.5s"
          repeatCount="indefinite"
        /></circle
      >
      <circle cx="30" cy="400" r="4" fill="#ffffff" opacity="0.3"
        ><animate
          attributeName="opacity"
          values="0.1;0.5;0.1"
          dur="7s"
          repeatCount="indefinite"
        /></circle
      >
      <circle cx="80" cy="520" r="2" fill="#ffffff" opacity="0.5"
        ><animate
          attributeName="opacity"
          values="0.2;0.7;0.2"
          dur="3.5s"
          repeatCount="indefinite"
        /></circle
      >
    </svg>
  </div>
  <!-- Right Plankton -->
  <div
    class="pointer-events-none absolute inset-y-0 right-0 z-10 hidden md:flex items-center"
  >
    <svg
      width="150"
      height="600"
      viewBox="0 0 150 600"
      xmlns="http://www.w3.org/2000/svg"
    >
      <circle cx="110" cy="120" r="2" fill="#ffffff" opacity="0.5"
        ><animate
          attributeName="opacity"
          values="0.2;0.7;0.2"
          dur="4.5s"
          repeatCount="indefinite"
        /></circle
      >
      <circle cx="50" cy="280" r="3" fill="#ffffff" opacity="0.4"
        ><animate
          attributeName="opacity"
          values="0.1;0.6;0.1"
          dur="6s"
          repeatCount="indefinite"
        /></circle
      >
      <circle cx="120" cy="450" r="4" fill="#ffffff" opacity="0.3"
        ><animate
          attributeName="opacity"
          values="0.2;0.5;0.2"
          dur="5s"
          repeatCount="indefinite"
        /></circle
      >
      <circle cx="70" cy="550" r="2" fill="#ffffff" opacity="0.6"
        ><animate
          attributeName="opacity"
          values="0.3;0.8;0.3"
          dur="4s"
          repeatCount="indefinite"
        /></circle
      >
    </svg>
  </div>

  <div
    class="relative z-30 flex w-[85vw] max-w-4xl flex-col overflow-hidden rounded-xl bg-[#15202B] text-slate-100 shadow-2xl ring-1 ring-white/10 md:w-[70vw]"
  >
    <!-- Top Window Bar -->
    <div
      class="flex h-10 w-full shrink-0 items-center justify-between border-b border-white/5 bg-[#1e293b] px-4 font-mono text-sm text-slate-300 shadow-sm"
    >
      <section id="work">
        <span>work</span>
      </section>
    </div>

    <div class="flex max-h-[80vh] flex-col overflow-y-auto p-8 md:p-12">
      <!-- Warning/Banner -->
      <div class="mb-10 rounded-lg bg-cyan-500/10 p-6 ring-1 ring-cyan-500/20">
        <p class="font-medium text-slate-200">
          Accepting work offers via my <a
            href="mailto:josephgabriemolina@gmail.com"
            class="text-cyan-200 hover:underline">work email</a
          >!<br />
          <span class="font-normal text-slate-400"
            >I do web design, and web/app/game development. :)</span
          >
        </p>
      </div>

      <!-- Tools & Dev Flex -->
      <div class="grid grid-cols-1 gap-12 lg:grid-cols-2">
        <!-- TOOLS -->
        <div>
          <h3
            class="mb-6 font-mono text-xl font-bold tracking-widest text-[#E2E8F0] uppercase"
          >
            TOOLS
          </h3>
          <div class="flex flex-wrap gap-2">
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >Adobe Photoshop</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >Nvim</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >Antigravity</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >Godot</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >Gimp</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >Procreate</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >Blender</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >Figma</span
            >
          </div>
        </div>

        <!-- DEVELOPMENT -->
        <div>
          <h3
            class="mb-6 font-mono text-xl font-bold tracking-widest text-[#E2E8F0] uppercase"
          >
            DEVELOPMENT
          </h3>
          <div class="flex flex-wrap gap-2">
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >Go</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >Pytho</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >C</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >C++</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >JavaScript</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >HTML/CSS</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >React</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >C#</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >Svelte</span
            >
            <span
              class="inline-flex cursor-default items-center rounded-md border border-slate-700 bg-slate-800 px-3 py-1 font-sans text-sm font-medium text-slate-300 shadow-sm transition-colors hover:bg-slate-700"
              >Typescript</span
            >
          </div>
        </div>
      </div>

      <!-- PROJECTS -->
      <h3
        class="mb-6 mt-16 font-mono text-xl font-bold uppercase tracking-widest text-[#E2E8F0]"
      >
        PROJECTS
      </h3>

      <div class="flex flex-col gap-12 pr-4">
        <!-- Project 1 -->
        <div class="flex flex-col gap-6 md:flex-row md:items-start md:gap-8">
          <!-- Project Image -->
          <div
            class="relative flex aspect-video w-full shrink-0 items-center justify-center overflow-hidden rounded-lg bg-slate-800 shadow-inner ring-4 ring-[#1e293b] md:w-80"
          >
            <!-- Add your image source below -->
            <img
              src="/images/arthas.png"
              alt="Arthas AI"
              class="h-full w-full object-cover"
            />
          </div>

          <!-- Project details -->
          <div class="flex flex-col">
            <h4
              class="font-sans text-3xl font-medium tracking-tight text-cyan-200"
            >
              Arthas AI
            </h4>
            <p class="mt-4 font-sans text-base leading-relaxed text-slate-300">
              I really love using AI, so i made an llm for research papers
            </p>
            <p class="mt-4 font-sans text-base leading-relaxed text-slate-300">
              I helped create the backend especifically the AI credits and
              feeding research paper. Free and available to download on
              <a href="/" class="text-cyan-200 underline hover:text-cyan-100"
                >Github</a
              >
            </p>
          </div>
        </div>

        <!-- Project 2 -->
        <div class="flex flex-col gap-6 md:flex-row md:items-start md:gap-8">
          <!-- Project Image -->
          <div
            class="relative flex aspect-video w-full shrink-0 items-center justify-center overflow-hidden rounded-lg bg-slate-800 shadow-inner ring-4 ring-[#1e293b] md:w-80"
          >
            <!-- Add your image source below -->
            <img
              src="/images/MTV.png"
              alt="School portal"
              class="h-full w-full object-cover"
            />
          </div>

          <!-- Project details -->
          <div class="flex flex-col">
            <h4
              class="font-sans text-3xl font-medium tracking-tight text-cyan-200"
            >
              School Portal
            </h4>
            <p class="mt-4 font-sans text-base leading-relaxed text-slate-300">
              I was contracted to create a school portal for a client.
            </p>
            <p class="mt-4 font-sans text-base leading-relaxed text-slate-300">
              I created and architected the entire system using svelte and
              convex . Check at <a
                href="/"
                class="text-cyan-200 underline hover:text-cyan-100"
                >github.com</a
              > for more information
            </p>
          </div>
        </div>

        <!-- Project 3 -->
        <div class="flex flex-col gap-6 md:flex-row md:items-start md:gap-8">
          <!-- Project Image -->
          <div
            class="relative flex aspect-video w-full shrink-0 items-center justify-center overflow-hidden rounded-lg bg-slate-800 shadow-inner ring-4 ring-[#1e293b] md:w-80"
          >
            <!-- Add your image source below -->
            <img
              src="/images/dialysisApp.png"
              alt="DialysisApp"
              class="h-full w-full object-cover"
            />
          </div>

          <!-- Project details -->
          <div class="flex flex-col">
            <h4
              class="font-sans text-3xl font-medium tracking-tight text-cyan-200"
            >
              DialysisApp
            </h4>
            <p class="mt-4 font-sans text-base leading-relaxed text-slate-300">
              I was contracted to create a dialysis app and website for a
              client.
            </p>
            <p class="mt-4 font-sans text-base leading-relaxed text-slate-300">
              I developed an App and a website for my client using React Native,
              svelte and convex. Check the demo at <a
                href="/"
                class="text-cyan-200 underline hover:text-cyan-100"
                >github.com</a
              > for more information
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<div
  bind:this={fishWrapper}
  class="pointer-events-none absolute left-0 w-full overflow-hidden z-20"
  style="top: 55vh; height: 140vh;"
>
  <!-- simplistic fish 1 -->
  <div
    class="pointer-events-none absolute text-cyan-300 transition-transform duration-75"
    style="left: {$c1.x}px; top: {$c1.y}px; transform: translate(-50%, -50%) rotate({a1}deg);"
  >
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="32"
      height="32"
      viewBox="0 0 24 24"
      fill="none"
      stroke="currentColor"
      stroke-width="2"
      stroke-linecap="round"
      stroke-linejoin="round"
    >
      <path d="M22 12c0 3-4 5-9 5s-9-2-9-5 4-5 9-5 9 2 9 5z" />
      <path d="M4 12L0 8v8z" fill="currentColor" stroke="none" />
      <circle cx="17" cy="12" r="1" fill="currentColor" />
    </svg>
  </div>
  <!-- simplistic fish 2 -->
  <div
    class="pointer-events-none absolute text-blue-300 transition-transform duration-75"
    style="left: {$c2.x}px; top: {$c2.y}px; transform: translate(-50%, -50%) rotate({a2}deg);"
  >
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="24"
      height="24"
      viewBox="0 0 24 24"
      fill="none"
      stroke="currentColor"
      stroke-width="2"
      stroke-linecap="round"
      stroke-linejoin="round"
    >
      <path d="M22 12c0 3-4 5-9 5s-9-2-9-5 4-5 9-5 9 2 9 5z" />
      <path d="M4 12L0 8v8z" fill="currentColor" stroke="none" />
      <circle cx="17" cy="12" r="1" fill="currentColor" />
    </svg>
  </div>
  <!-- simplistic fish 3 -->
  <div
    class="pointer-events-none absolute text-sky-400 transition-transform duration-75"
    style="left: {$c3.x}px; top: {$c3.y}px; transform: translate(-50%, -50%) rotate({a3}deg);"
  >
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="28"
      height="28"
      viewBox="0 0 24 24"
      fill="none"
      stroke="currentColor"
      stroke-width="2"
      stroke-linecap="round"
      stroke-linejoin="round"
    >
      <path d="M22 12c0 3-4 5-9 5s-9-2-9-5 4-5 9-5 9 2 9 5z" />
      <path d="M4 12L0 8v8z" fill="currentColor" stroke="none" />
      <circle cx="17" cy="12" r="1" fill="currentColor" />
    </svg>
  </div>
</div>

<style>
  :global(html) {
    scroll-behavior: smooth;
  }

  @keyframes fish-move {
    0% {
      transform: translateX(-1000px);
    }
    80% {
      transform: translateX(100vw);
    }
    100% {
      transform: translateX(100vw);
    }
  }

  .fish-container {
    animation: fish-move 12.5s linear infinite;
  }

  @keyframes wave-ripple {
    0% {
      transform: translateX(0);
    }
    100% {
      transform: translateX(-50%);
    }
  }

  .wave-svg {
    animation: wave-ripple 15s linear infinite;
  }
</style>
