<script lang="ts">
  let { item } = $props();
</script>

<div class="bg-white rounded-2xl p-5 border border-gray-100 shadow-sm hover:shadow-md transition duration-200 flex flex-col justify-between">
  <div>
    <!-- Gambar / Icon Box dengan Badge Biaya di Pojok Kanan Atas -->
    <div class="h-36 rounded-xl bg-gray-100 mb-4 overflow-hidden relative flex items-center justify-center border border-gray-200">
      <div class="text-center space-y-1">
        <span class="text-3xl">
          {#if item.category === 'Darurat Medis'}🏥
          {:else if item.category === 'Ambulans Gratis'}🚑
          {:else if item.category === 'SAR & Evakuasi'}🛶
          {:else}📦
          {/if}
        </span>
        <span class="text-[10px] text-gray-400 block font-medium uppercase tracking-wider">Aset Bantuan Siaga</span>
      </div>
      <div class="absolute top-2 right-2">
        <span class="{item.cost === 'Gratis' ? 'bg-emerald-50 text-emerald-700 border-emerald-200' : 'bg-blue-50 text-blue-700 border-blue-200'} text-[10px] font-bold px-2.5 py-0.5 rounded-md border shadow-sm bg-white">
          {item.cost}
        </span>
      </div>
    </div>

    <!-- Kategori & Status -->
    <div class="flex justify-between items-center mb-2">
      <span class="bg-red-50 text-red-600 text-[11px] font-semibold px-2.5 py-0.5 rounded-md">{item.category}</span>
      <span class="text-[11px] text-emerald-600 font-medium bg-emerald-50 px-2.5 py-0.5 rounded-md">🟢 {item.status}</span>
    </div>

    <!-- Judul & Instansi -->
    <h3 class="font-bold text-gray-900 text-base mb-1 hover:text-red-600 transition line-clamp-1">
      <a href="/listings/{item.id}">{item.title}</a>
    </h3>
    <p class="text-xs text-gray-500 mb-3">{item.instansi}</p>

    <!-- Lokasi & Telepon -->
    <div class="space-y-1.5 text-xs text-gray-600 border-t border-gray-100 pt-3">
      <div class="flex items-center gap-2"><span>📍</span><span class="line-clamp-1">{item.location}</span></div>
      <div class="flex items-center gap-2"><span>📞</span><span class="font-semibold text-gray-800">{item.phone}</span></div>
    </div>
  </div>

  <!-- Tombol Aksi Bawah -->
  <div class="mt-4 pt-3 border-t border-gray-100 flex items-center justify-between">
    <a href="/listings/{item.id}" class="text-xs font-bold text-red-600 hover:underline"> Lihat Detail ➔ </a>
    <a href="tel:{item.phone}" class="bg-red-600 hover:bg-red-700 text-white text-xs font-bold px-3 py-1.5 rounded-lg transition shadow-sm">
      📞 Hubungi
    </a>
  </div>
</div>
