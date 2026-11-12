<script lang="ts">
  import ListingCard from '../components/listings/ListingCard.svelte';
  import BlogCard from '../components/blog/BlogCard.svelte';

  // Data tiruan sementara untuk aset siaga
  const sampleListings = [
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
    }
  ];

  // Data tiruan sementara untuk artikel blog
  const sampleArticles = [
    { slug: 'detail', title: 'Panduan Pertolongan Pertama Korban Kecelakaan', summary: 'Langkah-langkah sigap dan aman saat menghadapi situasi darurat di jalan raya.', readTime: '3 min baca', category: 'Edukasi' },
    { slug: 'detail', title: 'Cara Sterilisasi Tabung Oksigen Darurat', summary: 'Tips merawat peralatan medis agar selalu steril dan siap digunakan sewaktu-waktu.', readTime: '4 min baca', category: 'Medis' },
    { slug: 'detail', title: 'Navigasi Evakuasi Saat Banjir Bandang', summary: 'Hal penting yang harus disiapkan sebelum dan sesudah evakuasi mandiri.', readTime: '5 min baca', category: 'Bencana' }
  ];
</script>

<div class="bg-gray-50 min-h-screen space-y-12 pb-12">
  <!-- Hero Section -->
  <section class="bg-gradient-to-b from-red-600 to-red-700 text-white py-12 sm:py-16 px-4 rounded-b-3xl shadow-lg relative overflow-hidden">
    <div class="container mx-auto max-w-4xl text-center space-y-6 relative z-10">
      <div class="inline-flex items-center gap-2 bg-white/10 backdrop-blur-md border border-white/20 px-3 py-1 rounded-full text-xs font-medium text-red-100">
        <span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span>
        <span>Platform Tanggap Bantuan Kemanusiaan & Darurat</span>
      </div>
      <h1 class="text-3xl sm:text-5xl font-black tracking-tight leading-tight">
        Cari Aset & Layanan Darurat <br class="hidden sm:inline">Cepat & Tepat di Sekitar Anda
      </h1>
      <p class="text-xs sm:text-base text-red-100 max-w-2xl mx-auto font-normal">
        Akses kilat ke posko bantuan, tabung oksigen, perahu evakuasi, hingga ambulans dari jaringan Mitra Penolong terpercaya.
      </p>

      <!-- Universal Search Box -->
      <div class="bg-white p-3 sm:p-4 rounded-2xl shadow-xl max-w-2xl mx-auto text-gray-800 space-y-3">
        <form class="flex flex-col sm:flex-row gap-2" action="/listings" method="GET">
          <div class="relative flex-1">
            <input type="text" name="q" placeholder="Ketik kata kunci (misal: 'oksigen', 'banyumas', 'ambulan')..." class="w-full pl-10 pr-4 py-3 rounded-xl border border-gray-200 text-xs sm:text-sm focus:outline-none focus:ring-2 focus:ring-red-500 font-medium">
            <span class="absolute left-3.5 top-3.5 text-base">🔍</span>
          </div>
          <button type="submit" class="bg-red-600 hover:bg-red-700 text-white font-bold text-xs sm:text-sm px-6 py-3 rounded-xl transition shadow-md flex items-center justify-center gap-2 shrink-0 cursor-pointer">
            <span>Cari Bantuan</span><span>➔</span>
          </button>
        </form>
        <div class="flex items-center gap-2 overflow-x-auto text-[11px] text-gray-500 pt-1 px-1">
          <span class="font-bold text-gray-400 shrink-0">Populer:</span>
          <a href="/listings?q=oksigen" class="bg-gray-100 hover:bg-red-50 hover:text-red-600 px-2.5 py-1 rounded-lg transition shrink-0 font-medium">Oksigen</a>
          <a href="/listings?q=ambulans" class="bg-gray-100 hover:bg-red-50 hover:text-red-600 px-2.5 py-1 rounded-lg transition shrink-0 font-medium">Ambulans</a>
          <a href="/listings?q=banyumas" class="bg-gray-100 hover:bg-red-50 hover:text-red-600 px-2.5 py-1 rounded-lg transition shrink-0 font-medium">Banyumas</a>
          <a href="/listings?q=sar" class="bg-gray-100 hover:bg-red-50 hover:text-red-600 px-2.5 py-1 rounded-lg transition shrink-0 font-medium">SAR</a>
        </div>
      </div>

      <!-- Tombol Unduh PWA / Akses Offline -->
      <div class="pt-2">
        <button onclick={() => alert('Fitur PWA siap diinstal! Versi Play Store & App Store akan segera hadir.')} class="inline-flex items-center gap-2 bg-amber-400 hover:bg-amber-500 text-gray-950 font-black text-xs sm:text-sm px-6 py-3 rounded-xl shadow-md transition cursor-pointer">
          <span>📱</span><span>Unduh PWA / Akses Offline (Segera di Play Store) ➔</span>
        </button>
      </div>
    </div>
  </section>

  <!-- Kategori Quick Access Grid -->
  <section class="container mx-auto px-4 max-w-5xl space-y-4">
    <div class="flex justify-between items-end">
      <div>
        <h2 class="text-xl font-bold text-gray-900">Kategori Bantuan Utama</h2>
        <p class="text-xs text-gray-500">Pilih jenis aset bantuan atau layanan yang dibutuhkan</p>
      </div>
      <a href="/categories" class="text-xs font-bold text-red-600 hover:underline">Lihat Semua Kategori ➔</a>
    </div>
    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3 sm:gap-4">
      <a href="/listings?category=Darurat+Medis" class="bg-white p-4 rounded-2xl border border-gray-100 shadow-sm hover:border-red-200 hover:shadow-md transition text-center space-y-2 group">
        <div class="text-3xl group-hover:scale-110 transition">🏥</div>
        <div class="font-bold text-xs text-gray-800 group-hover:text-red-600 transition">Darurat Medis</div>
      </a>
      <a href="/listings?category=Pemadam+Kebakaran" class="bg-white p-4 rounded-2xl border border-gray-100 shadow-sm hover:border-red-200 hover:shadow-md transition text-center space-y-2 group">
        <div class="text-3xl group-hover:scale-110 transition">🚒</div>
        <div class="font-bold text-xs text-gray-800 group-hover:text-red-600 transition">Pemadam Kebakaran</div>
      </a>
      <a href="/listings?category=SAR+Evakuasi" class="bg-white p-4 rounded-2xl border border-gray-100 shadow-sm hover:border-red-200 hover:shadow-md transition text-center space-y-2 group">
        <div class="text-3xl group-hover:scale-110 transition">🛶</div>
        <div class="font-bold text-xs text-gray-800 group-hover:text-red-600 transition">SAR & Evakuasi</div>
      </a>
      <a href="/listings?category=Posko+Bencana" class="bg-white p-4 rounded-2xl border border-gray-100 shadow-sm hover:border-red-200 hover:shadow-md transition text-center space-y-2 group">
        <div class="text-3xl group-hover:scale-110 transition">🏕️</div>
        <div class="font-bold text-xs text-gray-800 group-hover:text-red-600 transition">Posko Bencana</div>
      </a>
      <a href="/listings?category=Bantuan+Logistik" class="bg-white p-4 rounded-2xl border border-gray-100 shadow-sm hover:border-red-200 hover:shadow-md transition text-center space-y-2 group">
        <div class="text-3xl group-hover:scale-110 transition">📦</div>
        <div class="font-bold text-xs text-gray-800 group-hover:text-red-600 transition">Bantuan Logistik</div>
      </a>
      <a href="/listings?category=Ambulans+Gratis" class="bg-white p-4 rounded-2xl border border-gray-100 shadow-sm hover:border-red-200 hover:shadow-md transition text-center space-y-2 group">
        <div class="text-3xl group-hover:scale-110 transition">🚑</div>
        <div class="font-bold text-xs text-gray-800 group-hover:text-red-600 transition">Ambulans Gratis</div>
      </a>
    </div>
  </section>

  <!-- Section Aset Bantuan Terbaru -->
  <section class="container mx-auto px-4 max-w-5xl space-y-4">
    <div class="flex justify-between items-end">
      <div>
        <h2 class="text-xl font-bold text-gray-900">Aset Bantuan Siaga Terbaru</h2>
        <p class="text-xs text-gray-500">Aset dan layanan bantuan terkini dari Mitra Penolong</p>
      </div>
      <a href="/listings" class="text-xs font-bold text-red-600 hover:underline">Jelajahi Semua Aset ➔</a>
    </div>
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
      {#each sampleListings as item}
        <ListingCard {item} />
      {/each}
    </div>
  </section>

  <!-- Section Blog & Edukasi -->
  <section class="container mx-auto px-4 max-w-5xl space-y-6 pt-4">
    <div class="flex flex-col sm:flex-row sm:items-end justify-between gap-2 border-b border-gray-200/80 pb-3">
      <div>
        <span class="bg-red-50 text-red-600 text-[10px] font-bold px-2.5 py-0.5 rounded uppercase tracking-wider">Edukasi & Panduan Warga</span>
        <h2 class="text-xl sm:text-2xl font-black text-gray-900 mt-1">Artikel Tanggap Bencana & Tips Medis</h2>
        <p class="text-xs text-gray-500">Informasi penting seputar pertolongan pertama, navigasi bencana, dan panduan darurat.</p>
      </div>
      <a href="/blog" class="text-xs font-bold text-red-600 hover:underline shrink-0">Lihat Semua Artikel ➔</a>
    </div>
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
      {#each sampleArticles as article}
        <BlogCard {article} />
      {/each}
    </div>
  </section>
</div>
