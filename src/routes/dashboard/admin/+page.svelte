<script lang="ts">
  // Komponen khusus admin
</script>

<div class="space-y-6">
  <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
    <div class="bg-white p-5 rounded-2xl border border-gray-100 shadow-sm space-y-1">
      <span class="text-xs font-bold text-gray-400 block uppercase">Total Mitra Menunggu</span>
      <span class="text-2xl font-black text-amber-600">3 Pengajuan</span>
    </div>
    <div class="bg-white p-5 rounded-2xl border border-gray-100 shadow-sm space-y-1">
      <span class="text-xs font-bold text-gray-400 block uppercase">Total Daftar Bantuan</span>
      <span class="text-2xl font-black text-gray-900">24 Posko</span>
    </div>
    <div class="bg-white p-5 rounded-2xl border border-gray-100 shadow-sm space-y-1">
      <span class="text-xs font-bold text-gray-400 block uppercase">Artikel & Tips Publik</span>
      <span class="text-2xl font-black text-gray-900">8 Artikel</span>
    </div>
  </div>

  <div class="bg-white p-6 rounded-2xl border border-gray-100 shadow-sm space-y-4">
    <h3 class="font-bold text-gray-900 text-base">Moderasi Pengajuan Mitra Baru</h3>
    <p class="text-xs text-gray-500">Tinjau dan verifikasi posko atau relawan yang ingin bergabung sebagai Mitra Penolong.</p>
    
    <div class="p-4 bg-gray-50 rounded-xl border border-gray-100 flex items-center justify-between gap-4">
      <div class="space-y-0.5">
        <span class="text-xs font-bold text-gray-900 block">Posko SAR Banyemas Timur</span>
        <span class="text-[10px] text-gray-500">Kategori: SAR & Evakuasi • Diajukan oleh: Budi Santoso</span>
      </div>
      <div class="flex items-center gap-2">
        <button onclick={() => alert('Mitra disetujui!')} class="px-3 py-1.5 bg-green-600 hover:bg-green-700 text-white rounded-lg text-xs font-bold transition cursor-pointer">Setujui</button>
        <button onclick={() => alert('Mitra ditolak')} class="px-3 py-1.5 bg-red-100 hover:bg-red-200 text-red-700 rounded-lg text-xs font-bold transition cursor-pointer">Tolak</button>
      </div>
    </div>
  </div>
</div>
