<script lang="ts">
  import ListingCard from '../../components/listings/ListingCard.svelte';

  const allListings = [
    {
      id: 1,
      title: 'Tabung Oksigen 1m3 + Regulator',
      category: 'Darurat Medis',
      status: 'Ready',
      cost: 'Gratis',
      instansi: 'Relawan Kemanusiaan Purwokerto',
      location: 'Purwokerto Utara, Kab. Banyumas',
      phone: '081234567890'
    },
    {
      id: 2,
      title: 'Kursi Roda Lipat Standar Medis',
      category: 'Darurat Medis',
      status: 'Ready',
      cost: 'Sukarela',
      instansi: 'Budi Santoso (Personal)',
      location: 'Purwokerto Selatan, Kab. Banyumas',
      phone: '081987654321'
    },
    {
      id: 3,
      title: 'Ambulans Siaga 24 Jam Komunitas',
      category: 'Ambulans Gratis',
      status: 'Ready',
      cost: 'Gratis',
      instansi: 'Yayasan Ambulans Berkah',
      location: 'Wangon, Kab. Banyumas',
      phone: '081298765432'
    },
    {
      id: 4,
      title: 'Perahu Karet Evakuasi Banjir',
      category: 'SAR & Evakuasi',
      status: 'Ready',
      cost: 'Gratis',
      instansi: 'Komunitas SAR Lokal',
      location: 'Sumampir, Purwokerto Utara',
      phone: '085678901234'
    }
  ];

  let searchQuery = $state('');
  let selectedCategory = $state('Semua');

  const categories = [
    { name: 'Semua', label: 'Semua' },
    { name: 'Oksigen', label: 'Oksigen', icon: '💨', count: '1.4rb' },
    { name: 'Ambulans', label: 'Ambulans', icon: '🚑', count: '980' },
    { name: 'Kursi Roda', label: 'Kursi Roda', icon: '🦽', count: '650' },
    { name: 'Perahu Karet', label: 'Perahu Karet', icon: '🛶', count: '430' },
    { name: 'Tabung Gas', label: 'Tabung Gas', icon: '🔥', count: '310' }
  ];

  let filteredListings = $derived(
    allListings.filter((item) => {
      const matchQuery = 
        item.title.toLowerCase().includes(searchQuery.toLowerCase()) ||
        item.location.toLowerCase().includes(searchQuery.toLowerCase()) ||
        item.instansi.toLowerCase().includes(searchQuery.toLowerCase()) ||
        item.category.toLowerCase().includes(searchQuery.toLowerCase());

      if (selectedCategory === 'Semua') return matchQuery;
      return matchQuery && (
        item.title.toLowerCase().includes(selectedCategory.toLowerCase()) ||
        item.category.toLowerCase().includes(selectedCategory.toLowerCase())
      );
    })
  );
</script>

<div class="bg-gray-50 min-h-screen py-8">
  <div class="container mx-auto px-4 max-w-6xl space-y-8">
    <div>
      <a href="/" class="text-xs font-bold text-gray-600 hover:text-red-600 flex items-center gap-1"> ← Kembali ke Beranda </a>
    </div>

    <!-- Pusat Direktori & Pencarian Cerdas -->
    <div class="bg-white p-6 sm:p-8 rounded-2xl border border-gray-100 shadow-sm space-y-5">
      <div>
        <span class="bg-red-50 text-red-600 text-xs font-bold px-2.5 py-1 rounded-md uppercase tracking-wider"> Pusat Direktori & Pencarian Cerdas </span>
        <h1 class="text-2xl sm:text-3xl font-black text-gray-900 mt-2">Cari Aset, Alat, & Layanan Bantuan</h1>
        <p class="text-xs sm:text-sm text-gray-500 mt-1"> Ketik kata kunci apa saja atau pilih langsung dari tren pencarian warga yang paling sering dicari bulan ini. </p>
      </div>

      <!-- Input Search -->
      <div class="relative">
        <input 
          type="text" 
          bind:value={searchQuery}
          placeholder="Cari 'oksigen', 'ambulan', 'kursi roda', 'purwokerto', 'pmi'..." 
          class="w-full pl-11 pr-24 py-3.5 rounded-2xl border-2 border-red-100 text-xs sm:text-sm text-gray-900 focus:border-red-500 focus:ring-0 focus:outline-none transition shadow-sm font-medium"
        >
        <span class="absolute left-4 top-3.5 text-lg">🔍</span>
      </div>

      <!-- Tren / Filter Cepat -->
      <div class="flex items-center gap-2 overflow-x-auto pb-1 pt-1 scrollbar-none">
        <span class="text-xs font-bold text-gray-400 shrink-0 flex items-center gap-1"> 🔥 Tren Bulan Ini: </span>
        {#each categories as cat}
          <button 
            onclick={() => selectedCategory = cat.name}
            class="{selectedCategory === cat.name ? 'bg-red-600 text-white font-bold' : 'bg-orange-50 text-orange-800 border border-orange-100 hover:bg-orange-100 font-medium'} text-xs px-3.5 py-1.5 rounded-xl transition shrink-0 whitespace-nowrap cursor-pointer flex items-center gap-1"
          >
            {#if cat.icon}<span>{cat.icon}</span>{/if}
            <span>{cat.label}</span>
            {#if cat.count}<span class="text-[9px] opacity-70 bg-white/50 px-1.5 py-0.2 rounded-full font-bold">({cat.count})</span>{/if}
          </button>
        {/each}
      </div>
    </div>

    <!-- Informasi Jumlah Hasil -->
    <div class="flex justify-between items-center px-1">
      <p class="text-xs sm:text-sm text-gray-600 font-medium"> 
        Menampilkan <strong class="text-red-600">{filteredListings.length}</strong> hasil bantuan 
      </p>
    </div>

    <!-- Grid Listing / Kartu Bantuan -->
    {#if filteredListings.length > 0}
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        {#each filteredListings as item}
          <ListingCard {item} />
        {/each}
      </div>
    {:else}
      <div class="bg-white rounded-2xl p-12 text-center border border-gray-100 space-y-3 shadow-sm">
        <div class="text-4xl">🔍</div>
        <h3 class="font-bold text-gray-900 text-base">Tidak ada bantuan yang ditemukan</h3>
        <p class="text-xs text-gray-500">Coba gunakan kata kunci lain atau reset filter pencarian Anda.</p>
        <button onclick={() => { searchQuery = ''; selectedCategory = 'Semua'; }} class="mt-2 bg-red-600 text-white text-xs font-bold px-4 py-2 rounded-xl cursor-pointer">
          Reset Pencarian
        </button>
      </div>
    {/if}
  </div>
</div>
