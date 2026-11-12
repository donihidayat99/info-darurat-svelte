<script lang="ts">
  // Komponen khusus partner
</script>

<div class="space-y-6">
  <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4">
    <div>
      <h2 class="text-lg font-black text-gray-900">Kelola Posko & Daftar Bantuan</h2>
      <p class="text-xs text-gray-500">Kelola informasi posko dan layanan bantuan yang Anda publikasikan.</p>
    </div>
    <a href="/listings/create" class="bg-red-600 hover:bg-red-700 text-white font-black text-xs px-4 py-2.5 rounded-xl transition shadow-sm block text-center">
      + Tambah Daftar Bantuan Baru
    </a>
  </div>

  <div class="bg-white p-6 rounded-2xl border border-gray-100 shadow-sm space-y-4">
    <h3 class="font-bold text-gray-900 text-base">Daftar Bantuan yang Anda Unggah</h3>
    <div class="divide-y divide-gray-100">
      <div class="py-3 flex items-center justify-between gap-4">
        <div class="space-y-1">
          <span class="text-xs font-bold text-gray-900 block">Ambulans Siaga 24 Jam Purwokerto</span>
          <span class="text-[10px] bg-green-50 text-green-700 font-semibold px-2 py-0.5 rounded-full">Aktif & Terverifikasi</span>
        </div>
        <div class="flex items-center gap-2">
          <button onclick={() => alert('Fitur edit bantuan')} class="px-3 py-1.5 bg-gray-100 hover:bg-gray-200 text-gray-700 rounded-lg text-xs font-bold transition cursor-pointer">Edit</button>
          <button onclick={() => alert('Bantuan dihapus')} class="px-3 py-1.5 bg-red-50 hover:bg-red-100 text-red-600 rounded-lg text-xs font-bold transition cursor-pointer">Hapus</button>
        </div>
      </div>
    </div>
  </div>
</div>
