<script lang="ts">
  import { page } from '$app/state';
  import ListingCard from '../../../components/listings/ListingCard.svelte';

  // Data tiruan detail & database aset
  const itemsDatabase: Record<string, any> = {
    '1': {
      id: 1,
      title: 'Tabung Oksigen 1m3 + Regulator',
      category: 'Darurat Medis',
      status: 'Ready',
      cost: 'Gratis',
      location: 'Jl. Serayu, Sumampir, Purwokerto Utara, Banyumas',
      instansi: 'Relawan Kemanusiaan Purwokerto',
      ownership: 'Personal / Komunitas',
      coverage: 'Purwokerto & Sekitarnya',
      description: `Tersedia 2 unit tabung oksigen ukuran 1m3 lengkap dengan regulator dan selang baru. 

Bisa dipinjamkan gratis untuk warga yang membutuhkan kondisi darurat medis di wilayah Purwokerto dan sekitarnya. 

Syarat Peminjaman:
1. Menunjukkan KTP Peminjam.
2. Surat rujukan / keterangan butuh oksigen dari fasilitas kesehatan (jika ada).
3. Pengambilan mandiri ke lokasi penolong.`,
      contactType: 'Form Pesan (Privasi)',
      phone: '081234567890'
    },
    '2': {
      id: 2,
      title: 'Kursi Roda Lipat Standar Medis',
      category: 'Darurat Medis',
      status: 'Ready',
      cost: 'Sukarela',
      location: 'Purwokerto Selatan, Kab. Banyumas',
      instansi: 'Budi Santoso (Personal)',
      ownership: 'Personal',
      coverage: 'Kabupaten Banyumas',
      description: `Kursi roda lipat kondisi sangat baik dan bersih. Siap dipinjamkan bagi warga yang memerlukan untuk masa pemulihan atau darurat medis mendesak.`,
      contactType: 'WhatsApp Admin Otomatis',
      phone: '081987654321'
    },
    '3': {
      id: 3,
      title: 'Ambulans Siaga 24 Jam Komunitas',
      category: 'Ambulans Gratis',
      status: 'Ready',
      cost: 'Gratis',
      location: 'Wangon, Kab. Banyumas',
      instansi: 'Yayasan Ambulans Berkah',
      ownership: 'Yayasan / Organisasi',
      coverage: 'Wangon & Kabupaten Banyumas',
      description: `Layanan unit ambulans siaga darurat 24 jam untuk evakuasi pasien gawat darurat atau antar jemput jenazah dalam kota maupun luar kota.`,
      contactType: 'WhatsApp Admin Otomatis',
      phone: '081298765432'
    },
    '4': {
      id: 4,
      title: 'Perahu Karet Evakuasi Banjir',
      category: 'SAR & Evakuasi',
      status: 'Ready',
      cost: 'Gratis',
      location: 'Sumampir, Purwokerto Utara',
      instansi: 'Komunitas SAR Lokal',
      ownership: 'Komunitas Relawan',
      coverage: 'Banyumas & Sekitarnya',
      description: `Unit perahu karet lengkap dengan mesin tempel dan pelampung penyelamatan, siaga digerakkan jika terjadi kondisi darurat banjir bandang atau genangan tinggi.`,
      contactType: 'WhatsApp Admin Otomatis',
      phone: '085678901234'
    }
  };

  let itemId = $derived(page.params.id || '1');
  let item = $derived(itemsDatabase[itemId] || itemsDatabase['1']);

  // Ambil daftar bantuan terkait (selain item yang sedang dibuka)
  let relatedItems = $derived(
    Object.values(itemsDatabase).filter((i: any) => i.id !== Number(itemId)).slice(0, 3)
  );
</script>

<div class="bg-gray-50 min-h-screen py-8">
  <div class="container mx-auto px-4 max-w-5xl space-y-8">
    <!-- Top Nav Back -->
    <div class="flex items-center justify-between">
      <a href="/listings" class="text-xs font-bold text-gray-600 hover:text-red-600 flex items-center gap-1 cursor-pointer"> 
        ← Kembali ke Pencarian & Direktori 
      </a>
      <span class="text-xs text-gray-400">ID Aset: #{item.id}</span>
    </div>

    <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
      <!-- Kolom Kiri: Detail Utama Aset -->
      <div class="lg:col-span-8 space-y-6">
        <div class="bg-white p-6 sm:p-8 rounded-2xl border border-gray-100 shadow-sm space-y-4">
          <div class="flex flex-wrap justify-between items-center gap-2">
            <span class="bg-red-50 text-red-600 text-xs font-bold px-3 py-1 rounded-lg">{item.category}</span>
            <span class="bg-emerald-50 text-emerald-600 border-emerald-200 text-xs font-bold px-3 py-1 rounded-lg border">🟢 Siap Dipinjam / Digunakan</span>
          </div>

          <h1 class="text-2xl sm:text-3xl font-black text-gray-900 leading-tight">{item.title}</h1>
          <p class="text-xs text-gray-500 flex items-center gap-1"><span>📍</span> {item.location}</p>

          <!-- Gambar / Placeholder Foto Alat -->
          <div class="h-64 sm:h-80 bg-gray-100 rounded-xl overflow-hidden flex items-center justify-center border border-gray-200 text-gray-400 text-sm">
            🖼️ Foto Alat / Kendaraan Darurat
          </div>

          <!-- Deskripsi & Catatan Penolong -->
          <div class="border-t border-gray-100 pt-4 space-y-3">
            <h2 class="font-bold text-gray-900 text-base">Deskripsi & Catatan Penolong</h2>
            <p class="text-xs text-gray-600 leading-relaxed whitespace-pre-line">{item.description}</p>
          </div>

          <!-- Spesifikasi & Kondisi -->
          <div class="border-t border-gray-100 pt-4">
            <h2 class="font-bold text-gray-900 text-base mb-3">Spesifikasi & Kondisi</h2>
            <div class="grid grid-cols-2 sm:grid-cols-3 gap-3 text-xs">
              <div class="p-3 bg-gray-50 rounded-xl border border-gray-100">
                <span class="text-gray-400 block mb-1">Status Kepemilikan</span>
                <strong class="text-gray-800">{item.ownership}</strong>
              </div>
              <div class="p-3 bg-gray-50 rounded-xl border border-gray-100">
                <span class="text-gray-400 block mb-1">Biaya Layanan</span>
                <strong class="text-emerald-600">{item.cost}</strong>
              </div>
              <div class="p-3 bg-gray-50 rounded-xl border border-gray-100">
                <span class="text-gray-400 block mb-1">Cakupan Wilayah</span>
                <strong class="text-gray-800">{item.coverage}</strong>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Kolom Kanan: Informasi Penolong & Kontak -->
      <div class="lg:col-span-4 space-y-6">
        <div class="bg-white p-6 rounded-2xl border border-gray-100 shadow-sm space-y-4 sticky top-20">
          <h3 class="text-xs font-bold text-gray-400 uppercase tracking-wider">Informasi Penolong</h3>
          
          <div class="flex items-center gap-3">
            <div class="w-12 h-12 rounded-full bg-red-100 text-red-600 font-bold flex items-center justify-center text-lg">
              {item.instansi.charAt(0)}
            </div>
            <div>
              <h4 class="font-bold text-gray-900 text-sm">{item.instansi}</h4>
              <span class="text-xs text-emerald-600 font-medium">✓ Penolong Terverifikasi</span>
            </div>
          </div>

          <div class="border-t border-gray-100 pt-3 space-y-2 text-xs text-gray-600">
            <div class="flex justify-between"><span class="text-gray-400">Tipe Pendaftar:</span><span class="font-semibold text-gray-800">{item.ownership}</span></div>
            <div class="flex justify-between"><span class="text-gray-400">Saluran Kontak:</span><span class="font-semibold text-emerald-700">{item.contactType}</span></div>
          </div>

          <!-- Tombol Kontak WhatsApp Admin -->
          <div class="space-y-2 border-t border-gray-100 pt-4">
            <a href="https://wa.me/62{item.phone.replace(/^0/, '')}?text=Halo%20saya%20butuh%20bantuan%20terkait%20aset%20{encodeURIComponent(item.title)}" target="_blank" rel="noopener noreferrer" class="w-full bg-red-600 hover:bg-red-700 text-white font-bold py-3 px-4 rounded-xl text-xs transition duration-200 shadow-md flex items-center justify-center gap-2 cursor-pointer">
              💬 Hubungi via WhatsApp Admin
            </a>
          </div>

          <div class="p-3 bg-amber-50 rounded-xl border border-amber-200/60 text-[11px] text-amber-800">
            💡 <strong>Tips Keamanan:</strong> Selalu konfirmasi ketersediaan alat sebelum mendatangi lokasi. Jangan pernah mentransfer uang tanpa verifikasi resmi.
          </div>
        </div>
      </div>
    </div>

    <!-- Bagian Bantuan Terkait Lainnya (Related Listings) -->
    <section class="space-y-4 pt-4">
      <div class="flex items-center justify-between">
        <div>
          <h2 class="text-lg font-bold text-gray-900">Bantuan & Aset Terkait Lainnya</h2>
          <p class="text-xs text-gray-500">Opsi alternatif bantuan lain yang mungkin Anda butuhkan di sekitar wilayah ini.</p>
        </div>
        <a href="/listings" class="text-xs font-bold text-red-600 hover:underline">Lihat Semua ➔</a>
      </div>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        {#each relatedItems as related}
          <ListingCard item={related} />
        {/each}
      </div>
    </section>
  </div>
</div>
