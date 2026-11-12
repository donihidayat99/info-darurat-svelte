<script lang="ts">
  // State form pengajuan mitra
  let orgName = $state('');
  let category = $state('Medis & Ambulans');
  let phone = $state('');
  let address = $state('');
  let description = $state('');
  let hidePhone = $state(false); // Toggle privasi nomor WhatsApp

  function handleSubmit(e: Event) {
    e.preventDefault();
    alert(`Pengajuan Mitra Penolong untuk "${orgName}" berhasil dikirim! Menunggu verifikasi admin.`);
  }
</script>

<svelte:head>
  <title>Pendaftaran Mitra Penolong - Info Darurat</title>
</svelte:head>

<div class="max-w-2xl mx-auto px-4 py-8">
  <div class="bg-white p-8 rounded-2xl border border-gray-100 shadow-sm space-y-6">
    
    <!-- Header Informasi -->
    <div class="space-y-2 border-b border-gray-100 pb-6">
      <span class="bg-red-50 text-red-600 text-[10px] font-black px-3 py-1 rounded-full uppercase tracking-wider">Upgrade Akun</span>
      <h1 class="text-2xl font-black text-gray-900 tracking-tight">Formulir Pengajuan Mitra Penolong</h1>
      <p class="text-xs text-gray-500 leading-relaxed">
        Daftarkan posko, layanan medis, SAR, atau instansi relawan Anda agar dapat mempublikasikan daftar bantuan dan diakses warga secara langsung dalam situasi darurat.
      </p>
    </div>

    <!-- Form Pengajuan -->
    <form onsubmit={handleSubmit} class="space-y-4">
      
      <div class="space-y-1">
        <label class="text-xs font-bold text-gray-700" for="orgName">Nama Posko / Instansi / Layanan</label>
        <input id="orgName" type="text" bind:value={orgName} placeholder="cth. Posko Ambulans Sigap Purwokerto" required class="w-full px-3 py-2.5 rounded-xl border border-gray-200 text-xs focus:outline-none focus:ring-2 focus:ring-red-500">
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div class="space-y-1">
          <label class="text-xs font-bold text-gray-700" for="category">Kategori Layanan Utama</label>
          <select id="category" bind:value={category} class="w-full px-3 py-2.5 rounded-xl border border-gray-200 text-xs bg-white focus:outline-none focus:ring-2 focus:ring-red-500">
            <option value="Medis & Ambulans">Darurat Medis & Ambulans</option>
            <option value="Pemadam Kebakaran">Pemadam Kebakaran</option>
            <option value="SAR & Evakuasi">SAR & Evakuasi Bencana</option>
            <option value="Logistik & Dapur Umum">Logistik & Dapur Umum</option>
            <option value="Alat Berat / Teknis">Alat Berat / Bantuan Teknis</option>
          </select>
        </div>

        <div class="space-y-1">
          <label class="text-xs font-bold text-gray-700" for="phone">Nomor WhatsApp Resmi / Hotline</label>
          <input id="phone" type="text" bind:value={phone} placeholder="cth. 081234567890" required class="w-full px-3 py-2.5 rounded-xl border border-gray-200 text-xs focus:outline-none focus:ring-2 focus:ring-red-500">
        </div>
      </div>

      <!-- Pengaturan Privasi WhatsApp -->
      <div class="bg-gray-50 p-4 rounded-xl border border-gray-100 flex items-start gap-3">
        <input type="checkbox" id="hidePhone" bind:checked={hidePhone} class="mt-0.5 rounded border-gray-300 text-red-600 focus:ring-red-500">
        <div class="space-y-0.5 text-xs">
          <label for="hidePhone" class="font-bold text-gray-900 cursor-pointer">Sembunyikan Nomor WhatsApp Langsung</label>
          <p class="text-gray-500">Jika dicentang, nomor WhatsApp tidak langsung dipajang terbuka. Warga harus melalui tombol email atau formulir penghubung internal terlebih dahulu untuk menjaga privasi relawan.</p>
        </div>
      </div>

      <div class="space-y-1">
        <label class="text-xs font-bold text-gray-700" for="address">Alamat Lengkap / Cakupan Wilayah Posko</label>
        <textarea id="address" bind:value={address} rows="2" placeholder="cth. Jl. Jend. Soedirman No. 123, Purwokerto" required class="w-full px-3 py-2.5 rounded-xl border border-gray-200 text-xs focus:outline-none focus:ring-2 focus:ring-red-500"></textarea>
      </div>

      <div class="space-y-1">
        <label class="text-xs font-bold text-gray-700" for="description">Deskripsi Singkat & Jam Operasional</label>
        <textarea id="description" bind:value={description} rows="3" placeholder="cth. Melayani ambulans gratis 24 jam khusus wilayah Banyumas dan sekitarnya." required class="w-full px-3 py-2.5 rounded-xl border border-gray-200 text-xs focus:outline-none focus:ring-2 focus:ring-red-500"></textarea>
      </div>

      <div class="pt-2">
        <button type="submit" class="w-full bg-red-600 hover:bg-red-700 text-white font-black text-xs py-3 rounded-xl transition shadow-sm cursor-pointer">
          Kirim Pengajuan Mitra Penolong
        </button>
      </div>

    </form>

  </div>
</div>
