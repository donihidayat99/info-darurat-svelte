<script lang="ts">
  let title = $state('');
  let category = $state('Medis & Ambulans');
  let location = $state('');
  let contact = $state('');
  let description = $state('');

  function handleSubmit(e: Event) {
    e.preventDefault();
    alert(`Daftar bantuan "${title}" berhasil diunggah dan langsung aktif di direktori!`);
    // Di sini nanti bisa diarahkan balik ke dashboard mitra atau halaman list
  }
</script>

<svelte:head>
  <title>Tambah Daftar Bantuan Baru - Info Darurat</title>
</svelte:head>

<div class="max-w-2xl mx-auto px-4 py-8">
  <div class="bg-white p-8 rounded-2xl border border-gray-100 shadow-sm space-y-6">
    
    <!-- Header Informasi -->
    <div class="space-y-2 border-b border-gray-100 pb-6">
      <span class="bg-red-50 text-red-600 text-[10px] font-black px-3 py-1 rounded-full uppercase tracking-wider">Portal Mitra Penolong</span>
      <h1 class="text-2xl font-black text-gray-900 tracking-tight">Tambah Daftar Bantuan / Posko</h1>
      <p class="text-xs text-gray-500 leading-relaxed">
        Publikasikan informasi posko siaga, layanan evakuasi, atau logistik darurat yang dapat diakses langsung oleh warga secara real-time.
      </p>
    </div>

    <!-- Form Input Daftar Bantuan -->
    <form onsubmit={handleSubmit} class="space-y-4">
      
      <div class="space-y-1">
        <label class="text-xs font-bold text-gray-700" for="title">Judul Layanan / Posko</label>
        <input id="title" type="text" bind:value={title} placeholder="cth. Posko Evakuasi Darurat Bencana Slamet" required class="w-full px-3 py-2.5 rounded-xl border border-gray-200 text-xs focus:outline-none focus:ring-2 focus:ring-red-500">
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div class="space-y-1">
          <label class="text-xs font-bold text-gray-700" for="category">Kategori Layanan</label>
          <select id="category" bind:value={category} class="w-full px-3 py-2.5 rounded-xl border border-gray-200 text-xs bg-white focus:outline-none focus:ring-2 focus:ring-red-500">
            <option value="Medis & Ambulans">Darurat Medis & Ambulans</option>
            <option value="Pemadam Kebakaran">Pemadam Kebakaran</option>
            <option value="SAR & Evakuasi">SAR & Evakuasi Bencana</option>
            <option value="Logistik & Dapur Umum">Logistik & Dapur Umum</option>
            <option value="Alat Berat / Teknis">Alat Berat / Bantuan Teknis</option>
          </select>
        </div>

        <div class="space-y-1">
          <label class="text-xs font-bold text-gray-700" for="contact">Nomor Kontak / WhatsApp Posko</label>
          <input id="contact" type="text" bind:value={contact} placeholder="cth. 081234567890" required class="w-full px-3 py-2.5 rounded-xl border border-gray-200 text-xs focus:outline-none focus:ring-2 focus:ring-red-500">
        </div>
      </div>

      <div class="space-y-1">
        <label class="text-xs font-bold text-gray-700" for="location">Lokasi / Alamat Lengkap</label>
        <input id="location" type="text" bind:value={location} placeholder="cth. Jl. Raya Baturraden KM 7, Purwokerto" required class="w-full px-3 py-2.5 rounded-xl border border-gray-200 text-xs focus:outline-none focus:ring-2 focus:ring-red-500">
      </div>

      <div class="space-y-1">
        <label class="text-xs font-bold text-gray-700" for="description">Keterangan & Ketersediaan Layanan</label>
        <textarea id="description" bind:value={description} rows="4" placeholder="cth. Menyediakan tenda darurat, stok obat-obatan P3K, dan relawan siaga 24 jam." required class="w-full px-3 py-2.5 rounded-xl border border-gray-200 text-xs focus:outline-none focus:ring-2 focus:ring-red-500"></textarea>
      </div>

      <div class="pt-2 flex items-center gap-3">
        <a href="/dashboard" class="w-1/3 bg-gray-100 hover:bg-gray-200 text-gray-700 font-bold text-xs py-3 rounded-xl transition text-center">
          Batal
        </a>
        <button type="submit" class="w-2/3 bg-red-600 hover:bg-red-700 text-white font-black text-xs py-3 rounded-xl transition shadow-sm cursor-pointer">
          Publikasikan Bantuan
        </button>
      </div>

    </form>

  </div>
</div>
