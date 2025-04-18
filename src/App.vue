<script setup>
import { ref } from 'vue'

function toggleTheme() {
  const html = document.documentElement
  const isDark = html.classList.contains('dark')

  if (isDark) {
    html.classList.remove('dark')
    localStorage.theme = 'light'
  } else {
    html.classList.add('dark')
    localStorage.theme = 'dark'
  }
}

const sidebarOpen = ref(false)
</script>

<template>
  <div
    class="dark:text-white dark:bg-black bg-gray-100 min-h-screen flex flex-col md:flex-row dark:md:flex-row-reverse"
  >
    <!-- Mobile Header with Hamburger -->
    <div
      class="md:hidden flex items-center justify-between p-4 border-b border-zinc-200 dark:border-zinc-800"
    >
      <div class="text-xl font-bold">Darkmode Dash</div>
      <button @click="sidebarOpen = !sidebarOpen" aria-label="Toggle sidebar">
        <span class="material-icons">menu</span>
      </button>
    </div>

    <!-- Sidebar -->
    <aside
      class="w-full md:w-64 p-6 md:h-screen transition-all duration-300 sticky left-0 top-0 bg-gray-50 dark:bg-zinc-900"
      :class="{ hidden: !sidebarOpen, block: sidebarOpen, 'md:block': true }"
    >
      <div class="flex items-center justify-center mb-6">
        <div class="bg-gradient-to-br from-pink-500 to-purple-500 w-8 h-8 rounded-full mr-2"></div>
        <div class="text-xl font-bold">Darkmode Dash</div>
      </div>
      <nav class="space-y-2 text-sm">
        <a href="#" class="nav-item nav-item-active nav-item-hover">
          <span class="material-icons nav-item-icon-active">dashboard</span> Dashboard
        </a>
        <a href="#" class="nav-item nav-item-hover">
          <span class="material-icons nav-item-icon">table_chart</span> Tables
        </a>
        <a href="#" class="nav-item nav-item-hover">
          <span class="material-icons nav-item-icon">credit_card</span> Billing
        </a>
        <a href="#" class="nav-item nav-item-hover">
          <span class="material-icons nav-item-icon">handyman</span> RTL
        </a>
        <a href="#" class="nav-item nav-item-hover">
          <span class="material-icons nav-item-icon">vrpano</span> Virtual Reality
        </a>
        <div class="mt-6 text-xs uppercase text-zinc-500">Account Pages</div>
        <a
          href="#"
          class="flex items-center gap-3 px-3 py-2 rounded hover:bg-zinc-100 dark:hover:bg-zinc-800"
        >
          <span class="material-icons">person</span> Profile
        </a>
        <a
          href="#"
          class="flex items-center gap-3 px-3 py-2 rounded hover:bg-zinc-100 dark:hover:bg-zinc-800"
        >
          <span class="material-icons">login</span> Sign In
        </a>
      </nav>
    </aside>

    <!-- Main Content -->
    <main class="flex-1 p-6 space-y-6">
      <!-- Header -->
      <div class="flex items-center justify-between">
        <div class="flex items-center gap-3 w-full">
          <input type="text" placeholder="Search..." class="input" />
          <button
            @click="toggleTheme"
            class="flex items-center gap-1 px-1 py-1 rounded-full transition-colors border border-gray-300 dark:border-zinc-700"
            aria-label="Toggle dark mode"
          >
            <span
              class="material-icons w-7 h-7 flex items-center justify-center dark:text-zinc-600 transition-colors !text-lg rounded-full bg-white dark:bg-black"
              >light_mode</span
            >
            <span
              class="material-icons dark:text-white text-gray-400 w-7 h-7 flex items-center justify-center rounded-full transition-colors !text-lg dark:bg-zinc-900"
              >dark_mode</span
            >
          </button>
        </div>
      </div>

      <!-- Stat Cards -->
      <div
        class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 dark:grid-cols-2 gap-4 dark:font-mono"
      >
        <div class="dashboard-card">
          <div class="text-sm text-zinc-500">Today's Money</div>
          <div class="text-2xl font-bold text-green-500">
            $53,000 <span class="text-sm">+55%</span>
          </div>
        </div>
        <div class="dashboard-card">
          <div class="text-sm text-zinc-500">Today's Users</div>
          <div class="text-2xl font-bold text-green-500">
            2,300 <span class="text-sm">+3%</span>
          </div>
        </div>
        <div class="dashboard-card">
          <div class="text-sm text-zinc-500">New Clients</div>
          <div class="text-2xl font-bold text-red-500">+3,462 <span class="text-sm">-2%</span></div>
        </div>
        <div class="dashboard-card">
          <div class="text-sm text-zinc-500">Sales</div>
          <div class="text-2xl font-bold text-green-500">
            $103,430 <span class="text-sm">+5%</span>
          </div>
        </div>
      </div>

      <!-- Cards Row -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
        <div class="dashboard-card md:col-span-2">
          <span class="text-gray-500 uppercase text-xs font-semibold">Built as a demo</span>
          <div class="font-bold text-lg mb-2">Darkmode Dash</div>
          <p class="text-sm text-zinc-500 mb-2">
            This dashboard demos how to toggle between dark and light mode themes using tailwind.
            Notice how even the layout and fonts can be changed between themes.
          </p>
          <a href="#" class="text-sm text-primary font-medium">Read More →</a>
        </div>
        <div class="bg-gradient-to-br from-pink-500 to-purple-500 text-white rounded-xl p-6 shadow">
          <div class="text-lg font-bold">How It Works</div>
          <p class="text-sm">
            Tailwind provides a `dark:` variant that applies styles when the dark class is present
            on a parent element. We toggle that class using JavaScript to switch between light and
            dark themes dynamically.
          </p>
          <a href="#" class="text-sm font-semibold mt-2 inline-block">Read More →</a>
        </div>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div class="dashboard-card">
          <div class="font-bold">
            <code class="text-pink-500 p-2 rounded-md bg-gray-200 dark:bg-zinc-800"
              >tailwind.config.js</code
            >
          </div>
          <div class="mt-4">
            This CSS file imports Tailwind and defines a custom dark variant that applies styles
            when the `.dark` class is present anywhere up the DOM tree. Inside the `@layer`
            components block, it defines reusable utility classes using `@apply`, for example,
            `.dashboard-card` and `.nav-item`, which automatically adapt to light or dark mode based
            on the `.dark` class. This keeps your component styling consistent and theme-aware using
            just Tailwind utilities.
          </div>
        </div>
        <div class="dashboard-card">
          <div class="text-sm text-zinc-500">Some Javascript</div>
          <div>
            It is impossible to manually toggle between light and dark themes without a little JS.
            All you need is:
          </div>
          <div class="bg-zinc-100 dark:bg-zinc-800 rounded mt-4 p-4 overflow-auto">
            <pre class="text-sm text-zinc-800 dark:text-zinc-100 whitespace-pre" v-pre>
              <code>
function toggleTheme() {
  const html = document.documentElement
  const isDark = html.classList.contains('dark')

  if (isDark) {
    html.classList.remove('dark')
    localStorage.theme = 'light'
  } else {
    html.classList.add('dark')
    localStorage.theme = 'dark'
  }
}
              </code>
            </pre>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>
