<script lang="ts">
  // Data tiruan artikel edukasi & blog siaga bencana
  const allArticles = [
    {
      id: 1,
      title: 'Panduan Pertama Pemasangan & Pertolongan Tabung Oksigen di Rumah',
      category: 'Edukasi Medis',
      readTime: '3 menit baca',
      date: '24 Oktober 2026',
      summary: 'Langkah aman menggunakan regulator oksigen dan tindakan pencegahan kebocoran gas saat kondisi darurat keluarga.',
      icon: '🩺'
    },
    {
      id: 2,
      title: 'Persiapan Tas Siaga Bencana (Grab Bag) yang Wajib Ada di Rumah',
      category: 'Mitigasi Bencana',
      readTime: '5 menit baca',
      date: '25 Oktober 2026',
      summary: 'Daftar barang penting mulai dari dokumen penting, P3K, logistik kering, hingga cadangan air minum untuk 3 hari pertama evakuasi.',
      icon: '🎒'
    },
    {
      id: 3,
      title: 'Cara Aman Menghadapi Kebocoran Tabung Gas LPG agar Tidak Panik',
      category: 'Pencegahan',
      readTime: '4 min baca',
      date: '3 hari lalu',
      summary: 'Kenali tanda kebocoran gas, tindakan pertama mencabut regulator, membuka ventilasi, dan menghindari pemicu percikan api.',
      icon: '🔥'
    },
    {
      id: 4,
      title: 'Nomor Kontak Penting & Posko Evakuasi Darurat di Banyumas',
      category: 'Direktori Warga',
      readTime: '2 min baca',
      date: '1 minggu lalu',
      summary: 'Himpunan nomor darurat pemadam kebakaran, kepolisian, PMI, dan posko relawan kemanusiaan terdekat di wilayah Purwokerto dan sekitarnya.',
      icon: '📞'
    }
  ];

  let searchQuery = $state('');
  let selectedCategory = $state('Semua');

  const categories = ['Semua', 'Edukasi Medis', 'Mitigasi Bencana', 'Pencegahan', 'Direktori Warga'];

  let filteredArticles = $derived(
    allArticles.filter((article) => {
      const matchQuery = 
        article.title.toLowerCase().includes(searchQuery.toLowerCase()) ||
        article.summary.toLowerCase().includes(searchQuery.toLowerCase()) ||
        article.category.toLowerCase().includes(searchQuery.toLowerCase());

      if (selectedCategory === 'Semua') return matchQuery;
      return matchQuery && article.category.toLowerCase() === selectedCategory.toLowerCase();
    })
  );
</script>

<div class="bg-gray-50 min-h-screen py-8">
  <div class="container mx-auto px-4 max-w-6xl space-y-8">
    <div>
      <a href="/" class="text-xs font-bold text-gray-600 hover:text-red-600 flex items-center gap-1"> ← Kembali ke Beranda </a>
    </div>

    <!-- Header Pusat Edukasi & Pencarian -->
    <div class="bg-white p-6 sm:p-8 rounded-2xl border border-gray-100 shadow-sm space-y-5">
      <div>
        <span class="bg-red-50 text-red-600 text-xs font-bold px-2.5 py-1 rounded-md uppercase tracking-wider"> Pusat Edukasi Warga </span>
        <h1 class="text-2xl sm:text-3xl font-black text-gray-900 mt-2">Artikel Tanggap Bencana & Tips Medis</h1>
        <p class="text-xs sm:text-sm text-gray-500 mt-1"> Kumpulan panduan pertolongan pertama, pencegahan, dan informasi siaga darurat untuk keluarga. </p>
      </div>

      <!-- Input Search -->
      <div class="relative">
        <input 
          type="text" 
          bind:value={searchQuery}
          placeholder="Cari judul artikel atau topik siaga..." 
          class="w-full pl-11 pr-24 py-3.5 rounded-2xl border-2 border-red-100 text-xs sm:text-sm text-gray-900 focus:border-red-500 focus:ring-0 focus:outline-none transition shadow-sm font-medium"
        >
        <span class="absolute left-4 top-3.5 text-lg">🔍</span>
      </div>

      <!-- Filter Kategori Artikel -->
      <div class="flex items-center gap-2 overflow-x-auto pb-1 pt-1 scrollbar-none">
        <span class="text-xs font-bold text-gray-400 shrink-0"> Kategori: </span>
        {#each categories as cat}
          <button 
            onclick={() => selectedCategory = cat}
            class="{selectedCategory === cat ? 'bg-red-600 text-white font-bold' : 'bg-gray-100 text-gray-700 hover:bg-gray-200 font-medium'} text-xs px-3.5 py-1.5 rounded-xl transition shrink-0 whitespace-nowrap cursor-pointer"
          >
            {cat}
          </button>
        {/each}
      </div>
    </div>

    <!-- Informasi Jumlah Artikel -->
    <div class="flex justify-between items-center px-1">
      <p class="text-xs sm:text-sm text-gray-600 font-medium"> 
        Menampilkan <strong class="text-red-600">{filteredArticles.length}</strong> artikel edukasi 
      </p>
    </div>

    <!-- Grid Artikel -->
    {#if filteredArticles.length > 0}
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        {#each filteredArticles as article}
          <a href="/blog/{article.id}" class="bg-white rounded-2xl border border-gray-100 shadow-sm hover:shadow-md transition duration-200 overflow-hidden flex flex-col justify-between group cursor-pointer">
            <div>
              <!-- Thumbnail / Ilustrasi Artikel -->
              <div class="h-44 bg-gray-100 relative flex items-center justify-center overflow-hidden border-b border-gray-100">
                <div class="text-center p-4 space-y-1">
                  <div class="w-12 h-12 mx-auto rounded-xl bg-red-50 text-red-600 flex items-center justify-center text-2xl font-bold group-hover:scale-110 transition">
                    {article.icon}
                  </div>
                  <span class="text-[10px] text-gray-400 font-medium block">Info Darurat Edukasi</span>
                </div>
                <span class="absolute top-3 left-3 bg-white/90 backdrop-blur-md text-red-700 font-bold text-[10px] px-2.5 py-1 rounded-lg border border-red-100 shadow-sm">
                  {article.category}
                </span>
              </div>

              <!-- Konten Teks -->
              <div class="p-5 space-y-2">
                <div class="flex items-center justify-between text-[11px] text-gray-400 font-medium">
                  <span>⏱️ {article.readTime}</span>
                  <span>{article.date}</span>
                </div>
                <h3 class="font-bold text-sm text-gray-900 group-hover:text-red-600 transition line-clamp-2">
                  {article.title}
                </h3>
                <p class="text-xs text-gray-500 line-clamp-3 leading-relaxed">
                  {article.summary}
                </p>
              </div>
            </div>

            <!-- Tombol Aksi Bawah -->
            <div class="p-5 pt-0 mt-auto">
              <div class="pt-3 border-t border-gray-100 flex items-center justify-between">
                <span class="text-xs font-bold text-red-600 group-hover:underline flex items-center gap-1">
                  Baca Selengkapnya ➔
                </span>
              </div>
            </div>
          </a>
        {/each}
      </div>
    {:else}
      <div class="bg-white rounded-2xl p-12 text-center border border-gray-100 space-y-3 shadow-sm">
        <div class="text-4xl">📚</div>
        <h3 class="font-bold text-gray-900 text-base">Artikel tidak ditemukan</h3>
        <p class="text-xs text-gray-500">Coba gunakan kata kunci lain atau pilih kategori "Semua".</p>
        <button onclick={() => { searchQuery = ''; selectedCategory = 'Semua'; }} class="mt-2 bg-red-600 text-white text-xs font-bold px-4 py-2 rounded-xl cursor-pointer">
          Reset Pencarian
        </button>
      </div>
    {/if}
  </div>
</div>
