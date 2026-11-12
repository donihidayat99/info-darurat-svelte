<script lang="ts">
  import { page } from '$app/state';

  let isMobileMenuOpen = $state(false);

  const isActive = (path: string) => page.url.pathname === path;
  const isListingActive = () => page.url.pathname.startsWith('/listings');
  const isBlogActive = () => page.url.pathname.startsWith('/blog');

  $effect(() => {
    page.url.pathname;
    isMobileMenuOpen = false;
  });
</script>

<header class="bg-white border-b border-gray-100 sticky top-0 z-40 shadow-sm">
  <div class="container mx-auto px-4 max-w-7xl h-16 flex items-center justify-between gap-4">
    <!-- Logo -->
    <a href="/" class="flex items-center gap-2 shrink-0">
      <div class="w-9 h-9 rounded-xl bg-red-600 text-white font-black text-lg flex items-center justify-center shadow-sm">🚨</div> 
      <div>
        <span class="font-black text-base text-gray-900 tracking-tight block leading-none">Info<span class="text-red-600">Darurat</span></span> 
        <span class="text-[9px] font-semibold text-gray-400 block tracking-wider uppercase">Tanggap Bantuan Warga</span>
      </div>
    </a> 

    <!-- Navigasi Menu Utama (Desktop) -->
    <nav class="hidden md:flex items-center gap-6 text-xs font-bold text-gray-600">
      <a href="/" class="transition {isActive('/') ? 'text-red-600 font-black' : 'hover:text-red-600'}">Beranda</a> 
      <a href="/listings" class="transition {isListingActive() ? 'text-red-600 font-black' : 'hover:text-red-600'}">Daftar Bantuan</a> 
      <a href="/categories" class="transition {isActive('/categories') ? 'text-red-600 font-black' : 'hover:text-red-600'}">Kategori</a> 
      <a href="/blog" class="transition {isBlogActive() ? 'text-red-600 font-black' : 'hover:text-red-600'}">Artikel</a> 
      <a href="/donation" class="transition {isActive('/donation') ? 'text-red-600 font-black' : 'hover:text-red-600'}">Dukung Kami</a>
    </nav> 

    <!-- Tombol Aksi Kanan (Desktop) - Fokus ke Direktori & Portal Mitra -->
    <div class="hidden md:flex items-center gap-3">
      <a href="/dashboard" class="bg-gray-100 hover:bg-gray-200 text-gray-800 text-xs font-bold px-3 py-2 rounded-xl transition shadow-sm flex items-center gap-1.5">
        <span>👤</span><span>Dashboard</span>
      </a>
      <a href="/auth/login" class="bg-red-600 hover:bg-red-700 text-white text-xs font-bold px-4 py-2 rounded-xl transition shadow-sm flex items-center gap-1.5">
        <span>🤝</span><span>Portal Mitra</span>
      </a>
    </div> 

    <!-- Tombol Mobile Menu -->
    <button 
      type="button"
      onclick={() => isMobileMenuOpen = !isMobileMenuOpen}
      class="md:hidden p-2 rounded-xl bg-gray-100 text-gray-700 hover:bg-gray-200 transition text-lg cursor-pointer"
      aria-label="Toggle Menu"
    >
      {isMobileMenuOpen ? '✕' : '☰'}
    </button>
  </div>

  <!-- Dropdown Menu Mobile -->
  {#if isMobileMenuOpen}
    <div class="md:hidden bg-white border-b border-gray-100 px-4 py-4 space-y-3 shadow-lg transition-all">
      <nav class="flex flex-col space-y-3 text-xs font-bold text-gray-700 pb-3 border-b border-gray-100">
        <a href="/" class="py-1 transition {isActive('/') ? 'text-red-600 font-black' : 'hover:text-red-600'}">Beranda</a> 
        <a href="/listings" class="py-1 transition {isListingActive() ? 'text-red-600 font-black' : 'hover:text-red-600'}">Daftar Bantuan</a> 
        <a href="/categories" class="transition {isActive('/categories') ? 'text-red-600 font-black' : 'hover:text-red-600'}">Kategori</a> 
        <a href="/blog" class="transition {isBlogActive() ? 'text-red-600 font-black' : 'hover:text-red-600'}">Artikel</a> 
        <a href="/donation" class="transition {isActive('/donation') ? 'text-red-600 font-black' : 'hover:text-red-600'}">Dukung Kami</a>
      </nav>

      <div class="flex flex-col gap-2 pt-1">
        <a href="/dashboard" class="bg-gray-100 hover:bg-gray-200 text-gray-800 text-xs font-bold py-2.5 rounded-xl transition text-center shadow-sm flex items-center justify-center gap-1.5">
          <span>👤</span><span>Dashboard Pengguna</span>
        </a> 
        <a href="/auth/login" class="bg-red-600 hover:bg-red-700 text-white text-xs font-bold py-2.5 rounded-xl transition text-center shadow-sm flex items-center justify-center gap-1.5">
          <span>🤝</span><span>Portal Mitra</span>
        </a>
      </div>
    </div>
  {/if}
</header>
