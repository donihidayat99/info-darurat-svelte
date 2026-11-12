<script lang="ts">
  const categoriesList = [
    {
      id: 'medis',
      name: 'Darurat Medis',
      description: 'Tabung oksigen, regulator, alat medis darurat',
      icon: '🏥',
      count: '124 Aset',
      query: 'medis'
    },
    {
      id: 'pemadam',
      name: 'Pemadam Kebakaran',
      description: 'Posko & armada penanganan pemadam kebakaran',
      icon: '🚒',
      count: '45 Aset',
      query: 'pemadam'
    },
    {
      id: 'sar',
      name: 'SAR & Evakuasi',
      description: 'Perahu karet, pelampung, perlengkapan SAR',
      icon: '🛶',
      count: '88 Aset',
      query: 'sar'
    },
    {
      id: 'posko',
      name: 'Posko Bencana',
      description: 'Tenda pengungsian & tempat penampungan darurat',
      icon: '🏕️',
      count: '32 Aset',
      query: 'posko'
    },
    {
      id: 'logistik',
      name: 'Bantuan Logistik',
      description: 'Bahan makanan, selimut, air bersih, & pakaian',
      icon: '📦',
      count: '95 Aset',
      query: 'logistik'
    },
    {
      id: 'ambulans',
      name: 'Ambulans Gratis',
      description: 'Layanan armada ambulans bantuan kemanusiaan',
      icon: '🚑',
      count: '76 Aset',
      query: 'ambulans'
    }
  ];
</script>

<div class="bg-gray-50 min-h-screen py-8">
  <!-- Menggunakan max-w-6xl dan space-y-8 persis seperti halaman blog -->
  <div class="container mx-auto px-4 max-w-6xl space-y-8">
    <div>
      <a href="/" class="text-xs font-bold text-gray-600 hover:text-red-600 flex items-center gap-1"> 
        ← Kembali ke Beranda 
      </a>
    </div>

    <!-- Header Kategori -->
    <div class="bg-white p-6 sm:p-8 rounded-2xl border border-gray-100 shadow-sm space-y-2">
      <span class="bg-red-50 text-red-600 text-xs font-bold px-2.5 py-1 rounded-md uppercase tracking-wider"> Direktori Kategori Bantuan </span>
      <h1 class="text-2xl sm:text-3xl font-black text-gray-900">Seluruh Kategori Aset & Layanan Darurat</h1>
      <p class="text-xs sm:text-sm text-gray-500"> Pilih kategori di bawah untuk menemukan ketersediaan tabung oksigen, armada evakuasi, ambulans, hingga logistik terdekat. </p>
    </div>

    <!-- Grid Kategori -->
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
      {#each categoriesList as cat}
        <a href="/listings?q={cat.query}" class="bg-white p-5 rounded-2xl border border-gray-100 shadow-sm hover:border-red-300 hover:shadow-md transition cursor-pointer flex items-center justify-between group">
          <div class="flex items-center gap-4">
            <div class="w-12 h-12 rounded-2xl bg-red-50 text-red-600 flex items-center justify-center text-2xl group-hover:scale-110 transition shrink-0">
              {cat.icon}
            </div>
            <div>
              <h3 class="font-bold text-sm text-gray-900 group-hover:text-red-600 transition">{cat.name}</h3>
              <p class="text-xs text-gray-400 mt-0.5 leading-snug">{cat.description}</p>
            </div>
          </div>
          <div class="text-right shrink-0 pl-2">
            <span class="text-xs font-bold text-gray-700 bg-gray-50 px-2.5 py-1 rounded-lg border border-gray-100 block mb-1">
              {cat.count}
            </span>
            <span class="text-[10px] text-red-600 font-bold group-hover:underline block">Lihat ➔</span>
          </div>
        </a>
      {/each}
    </div>

    <!-- Banner Bawah -->
    <div class="bg-red-600 text-white p-6 rounded-2xl shadow-md flex flex-col sm:flex-row justify-between items-center gap-4">
      <div class="space-y-1 text-center sm:text-left">
        <h3 class="font-bold text-base text-white">Tidak Menemukan Kategori yang Sesuai?</h3>
        <p class="text-xs text-red-100">Gunakan fitur Pencarian Cerdas Universal untuk menemukan alat atau mitra berdasarkan kata kunci bebas.</p>
      </div>
      <a href="/listings" class="bg-white text-red-600 font-bold text-xs px-5 py-3 rounded-xl shadow hover:bg-red-50 transition shrink-0"> 
        🔍 Buka Pencarian Universal 
      </a>
    </div>
  </div>
</div>
