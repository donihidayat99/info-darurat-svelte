<script lang="ts">
  // Data progress penggalangan dana operasional
  let currentFunds = 3850000;
  let targetFunds = 5000000;
  let percentage = Math.round((currentFunds / targetFunds) * 100);

  // Daftar riwayat dukungan terbaru (mock data)
  const recentSupporters = [
    { name: "Hamba Allah", amount: "Rp 150.000", time: "10 menit lalu", message: "Semoga berkah untuk operasional posko!" },
    { name: "Rian Pratama", amount: "Rp 50.000", time: "1 jam lalu", message: "Sehat selalu para relawan Info Darurat." },
    { name: "Keluarga Besar Purwokerto", amount: "Rp 500.000", time: "3 jam lalu", message: "Dukungan server bulanan." },
    { name: "Siti Aminah", amount: "Rp 100.000", time: "5 jam lalu", message: "Terima kasih infonya sangat membantu." }
  ];
</script>

<svelte:head>
  <title>Dukung Kami & Donasi Operasional - Info Darurat</title>
</svelte:head>

<div class="max-w-4xl mx-auto px-4 py-8 space-y-10">
  
  <!-- Header / Judul Halaman -->
  <div class="text-center space-y-3">
    <span class="bg-red-100 text-red-700 text-xs font-black px-3 py-1 rounded-full uppercase tracking-wider">Kemandirian Platform</span>
    <h1 class="text-3xl md:text-4xl font-black text-gray-900 tracking-tight">Dukung Operasional Info Darurat</h1>
    <p class="text-sm text-gray-600 max-w-2xl mx-auto leading-relaxed">
      Info Darurat dikembangkan sebagai platform digital terbuka yang independen. Bantuan dan dukungan Anda sepenuhnya dialokasikan untuk biaya server, pemeliharaan data posko, dan pengembangan fitur siaga warga.
    </p>
  </div>

  <!-- Grid Utama: Progress & QR Code Saweria -->
  <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
    
    <!-- Kolom Kiri & Tengah: Target Dana & Info -->
    <div class="md:col-span-2 space-y-6">
      
      <!-- Card Progress Bar -->
      <div class="bg-white p-6 rounded-2xl border border-gray-100 shadow-sm space-y-5">
        <div class="flex justify-between items-end">
          <div>
            <span class="text-xs font-bold text-gray-400 block uppercase tracking-wider">Target Bulanan (Server & Pemeliharaan)</span>
            <span class="text-2xl font-black text-gray-900">Rp {currentFunds.toLocaleString('id-ID')}</span>
          </div>
          <span class="text-sm font-bold text-red-600">Target: Rp {targetFunds.toLocaleString('id-ID')} ({percentage}%)</span>
        </div>

        <!-- Progress Bar Custom -->
        <div class="w-full bg-gray-100 h-4 rounded-full overflow-hidden p-0.5">
          <div class="bg-red-600 h-full rounded-full transition-all duration-500" style="width: {percentage}%"></div>
        </div>

        <p class="text-xs text-gray-500 leading-relaxed">
          Periode donasi terbuka setiap bulannya untuk memastikan sistem tetap aktif tanpa jeda iklan komersial yang mengganggu kecepatan akses darurat.
        </p>
      </div>

      <!-- Kenapa Mendukung Kami? -->
      <div class="bg-white p-6 rounded-2xl border border-gray-100 shadow-sm space-y-4">
        <h3 class="font-bold text-gray-900 text-base">Alokasi Penggunaan Dana</h3>
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 text-xs text-gray-600">
          <div class="p-3 bg-gray-50 rounded-xl space-y-1 border border-gray-100">
            <span class="font-bold text-gray-900 block">☁️ Infrastruktur Server</span>
            <p>Menjamin latensi rendah dan ketersediaan uptime 99.9% saat diakses warga dalam situasi mendesak.</p>
          </div>
          <div class="p-3 bg-gray-50 rounded-xl space-y-1 border border-gray-100">
            <span class="font-bold text-gray-900 block">🛠️ Pengembangan Fitur</span>
            <p>Peningkatan fitur pemetaan geografis, integrasi kontak darurat, dan optimasi versi PWA offline.</p>
          </div>
        </div>
      </div>

    </div>

    <!-- Kolom Kanan: QR Code Saweria / Tombol Donasi -->
    <div class="bg-white p-6 rounded-2xl border border-gray-100 shadow-sm text-center flex flex-col justify-between space-y-6">
      <div>
        <span class="text-xs font-bold text-red-600 bg-red-50 px-2.5 py-1 rounded-md uppercase">Scan QR / Saweria</span>
        <h3 class="font-bold text-gray-900 text-base mt-2">Dukung Lewat Saweria</h3>
        <p class="text-xs text-gray-500 mt-1">Mendukung semua e-Wallet (QRIS: GoPay, OVO, DANA, LinkAja) & Transfer Bank.</p>
      </div>

      <!-- Simulasi Kotak QR Code -->
      <div class="bg-gray-50 p-4 rounded-xl border border-dashed border-gray-300 flex flex-col items-center justify-center space-y-2">
        <div class="w-36 h-36 bg-white p-2 rounded-lg shadow-sm border border-gray-200 flex items-center justify-center">
          <div class="text-center space-y-1">
            <span class="text-3xl">📷</span>
            <span class="text-[10px] font-bold text-gray-400 block tracking-tight">QRIS SAWERIA</span>
          </div>
        </div>
        <span class="text-[10px] text-gray-400 font-medium">Scan menggunakan aplikasi bank/e-wallet apa saja</span>
      </div>

      <a href="https://saweria.co" target="_blank" rel="noopener noreferrer" class="w-full bg-red-600 hover:bg-red-700 text-white font-black text-xs py-3 rounded-xl transition shadow-sm block text-center">
        Buka Halaman Saweria ↗
      </a>
    </div>

  </div>

  <!-- Daftar Pendukung Terbaru -->
  <div class="bg-white p-6 rounded-2xl border border-gray-100 shadow-sm space-y-4">
    <h3 class="font-bold text-gray-900 text-base flex items-center gap-2">
      <span>🤝</span> Daftar Pendukung Terbaru
    </h3>
    <div class="divide-y divide-gray-100">
      {#each recentSupporters as sup}
        <div class="py-3 flex items-center justify-between gap-4">
          <div class="space-y-0.5">
            <div class="flex items-center gap-2">
              <span class="text-xs font-bold text-gray-900">{sup.name}</span>
              <span class="text-[10px] bg-green-50 text-green-700 font-semibold px-2 py-0.5 rounded-full">{sup.amount}</span>
            </div>
            <p class="text-xs text-gray-500 italic">"{sup.message}"</p>
          </div>
          <span class="text-[10px] text-gray-400 shrink-0">{sup.time}</span>
        </div>
      {/each}
    </div>
  </div>

  <!-- Call to Action Survey -->
  <div class="bg-gray-900 text-white p-6 rounded-2xl shadow-sm text-center space-y-3">
    <h4 class="font-bold text-sm">Bagaimana Pendapat Anda Tentang Halaman Ini?</h4>
    <p class="text-xs text-gray-400 max-w-lg mx-auto">Kami terus berupaya menyempurnakan transparansi platform. Bantu kami dengan mengisi survei singkat kepuasan pengguna.</p>
    <button onclick={() => alert('Terima kasih atas kesediaan mengisi survei!')} class="bg-amber-400 hover:bg-amber-500 text-gray-950 font-black text-xs px-5 py-2.5 rounded-xl transition cursor-pointer">
      Isi Survei Kepuasan
    </button>
  </div>

</div>
