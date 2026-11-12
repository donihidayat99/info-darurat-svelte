<script lang="ts">
  import { page } from '$app/state';

  // Database tiruan artikel edukasi
  const articlesDatabase: Record<string, any> = {
    '1': {
      id: 1,
      title: 'Panduan Pertama Pemasangan & Pertolongan Tabung Oksigen di Rumah',
      category: 'Edukasi Medis',
      date: '24 Oktober 2026',
      readTime: '3 menit baca',
      subtitle: 'Langkah aman menggunakan regulator oksigen dan tindakan pencegahan kebocoran gas saat kondisi darurat keluarga.',
      content: `Dalam situasi darurat medis yang melibatkan sesak napas berat, ketersediaan tabung oksigen portabel di rumah sangat krusial. Namun, penggunaan alat ini tidak boleh sembarangan dan harus memperhatikan standar keselamatan dasar.

1. Pengecekan Tekanan Tabung & Regulator
Pastikan jarum indikator pada regulator menunjukkan angka hijau (tekanan penuh). Jauhkan tabung oksigen dari sumber api terbuka, kompor, atau percikan listrik karena oksigen mempercepat proses pembakaran.

2. Pemasangan Selang Nasal Cannula
Atur aliran meteran sesuai anjuran medis (umumnya 2-4 liter per menit untuk pertolongan pertama). Bersihkan selang secara berkala dan pastikan posisi duduk pasien rileks.`
    },
    '2': {
      id: 2,
      title: 'Persiapan Tas Siaga Bencana (Grab Bag) yang Wajib Ada di Rumah',
      category: 'Mitigasi Bencana',
      date: '25 Oktober 2026',
      readTime: '5 menit baca',
      subtitle: 'Daftar barang penting mulai dari dokumen penting, P3K, logistik kering, hingga cadangan air minum untuk 3 hari pertama evakuasi.',
      content: `Tas siaga bencana atau grab bag sangat penting dipersiapkan di tempat yang mudah dijangkau sebelum bencana terjadi.

1. Dokumen Penting
Simpan fotokopi KTP, KK, sertifikat tanah, dan polis asuransi dalam kantong plastik kedap air.

2. Perlengkapan P3K & Obat Pribadi
Sediakan obat-obatan rutin keluarga serta perban, antiseptik, dan alat pengukur tekanan darah portabel.`
    }
  };

  let articleId = $derived(page.params.id || '1');
  let article = $derived(articlesDatabase[articleId] || articlesDatabase['1']);

  // Artikel terkait lainnya
  let relatedArticles = Object.values(articlesDatabase).filter((a: any) => a.id !== Number(articleId));
</script>

<div class="bg-gray-50 min-h-screen py-8">
  <div class="container mx-auto px-4 max-w-4xl space-y-8">
    <div>
      <a href="/blog" class="text-xs font-bold text-gray-600 hover:text-red-600 flex items-center gap-1"> 
        ← Kembali ke Daftar Artikel 
      </a>
    </div>

    <!-- Konten Utama Artikel -->
    <article class="bg-white p-6 sm:p-10 rounded-2xl border border-gray-100 shadow-sm space-y-6">
      <div class="space-y-3 border-b border-gray-100 pb-6">
        <div class="flex flex-wrap items-center gap-3 text-xs text-gray-500">
          <span class="bg-red-50 text-red-600 font-bold px-3 py-1 rounded-lg">{article.category}</span>
          <span>📅 {article.date}</span>
          <span>⏱️ {article.readTime}</span>
        </div>
        <h1 class="text-2xl sm:text-4xl font-black text-gray-900 leading-tight">{article.title}</h1>
        <p class="text-sm sm:text-base text-gray-600 leading-relaxed font-normal">{article.subtitle}</p>
      </div>

      <div class="space-y-4 text-xs sm:text-sm text-gray-800 leading-relaxed whitespace-pre-line">
        {article.content}
      </div>

      <!-- Call to Action Banner -->
      <div class="p-4 bg-red-50 rounded-2xl border border-red-100 flex flex-col sm:flex-row items-center justify-between gap-4">
        <div class="space-y-0.5 text-center sm:text-left">
          <h4 class="font-bold text-red-900 text-sm">Butuh Peminjaman Tabung Oksigen Terdekat?</h4>
          <p class="text-xs text-red-700">Cari penyedia tabung oksigen gratis atau sukarela di wilayah Banyumas.</p>
        </div>
        <a href="/listings?q=oksigen" class="bg-red-600 hover:bg-red-700 text-white font-bold text-xs px-5 py-2.5 rounded-xl shadow transition shrink-0">
          Cari Tabung Oksigen ➔
        </a>
      </div>
    </article>

    <!-- Bagian Related Posts / Artikel Terkait -->
    <section class="space-y-4 pt-6 border-t border-gray-200">
      <h2 class="text-lg font-bold text-gray-900">Artikel Terkait Lainnya</h2>
      <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
        {#each relatedArticles as rel}
          <div class="bg-white rounded-2xl border border-gray-100 shadow-sm hover:shadow-md transition duration-200 overflow-hidden flex flex-col justify-between group">
            <div class="h-36 bg-gray-100 relative flex items-center justify-center overflow-hidden border-b border-gray-100">
              <div class="text-center p-4 space-y-1">
                <div class="w-10 h-10 mx-auto rounded-xl bg-red-50 text-red-600 flex items-center justify-center text-xl font-bold">📖</div>
              </div>
              <span class="absolute top-3 left-3 bg-white/90 backdrop-blur-md text-red-700 font-bold text-[10px] px-2.5 py-1 rounded-lg border border-red-100 shadow-sm">
                {rel.category}
              </span>
            </div>
            <div class="p-5 space-y-2 flex-1 flex flex-col justify-between">
              <div class="space-y-1.5">
                <div class="flex items-center justify-between text-[11px] text-gray-400 font-medium">
                  <span>⏱️ {rel.readTime}</span>
                  <span>{rel.date}</span>
                </div>
                <h3 class="font-bold text-sm text-gray-900 group-hover:text-red-600 transition line-clamp-2">
                  {rel.title}
                </h3>
              </div>
              <div class="pt-3 border-t border-gray-100 flex items-center justify-between">
                <a href="/blog/{rel.id}" class="text-xs font-bold text-red-600 hover:underline flex items-center gap-1">
                  Baca Selengkapnya ➔
                </a>
              </div>
            </div>
          </div>
        {/each}
      </div>
    </section>
  </div>
</div>
