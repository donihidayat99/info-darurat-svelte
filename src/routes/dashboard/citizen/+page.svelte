<script lang="ts">
  let { user } = $props();
</script>

<div class="space-y-6">
  <div class="bg-white p-6 rounded-2xl border border-gray-100 shadow-sm space-y-6">
    <h3 class="font-bold text-gray-900 text-base">Pengaturan Akun Warga</h3>
    
    <form class="space-y-4 max-w-xl">
      <div class="space-y-1">
        <label class="text-xs font-bold text-gray-700" for="edit-name">Nama Lengkap</label>
        <input id="edit-name" type="text" value={user.name} class="w-full px-3 py-2.5 rounded-xl border border-gray-200 text-xs focus:outline-none focus:ring-2 focus:ring-red-500">
      </div>
      <div class="space-y-1">
        <label class="text-xs font-bold text-gray-700" for="edit-email">Alamat Email</label>
        <input id="edit-email" type="email" value={user.email} class="w-full px-3 py-2.5 rounded-xl border border-gray-200 text-xs focus:outline-none focus:ring-2 focus:ring-red-500">
      </div>
      <button type="button" onclick={() => alert('Perubahan profil berhasil disimpan!')} class="bg-gray-900 hover:bg-gray-800 text-white font-bold text-xs px-5 py-2.5 rounded-xl transition cursor-pointer">
        Simpan Perubahan
      </button>
    </form>
  </div>

  <!-- Kotak Ajakan Upgrade Mitra -->
  <div class="bg-gradient-to-r from-red-600 to-red-700 text-white p-6 rounded-2xl shadow-sm flex flex-col md:flex-row items-center justify-between gap-6">
    <div class="space-y-2 text-center md:text-left">
      <span class="bg-white/20 text-white text-[10px] font-black px-3 py-1 rounded-full uppercase tracking-wider">Peluang Kontribusi</span>
      <h3 class="text-lg font-black">Punya Posko atau Layanan Bantuan Darurat?</h3>
      <p class="text-xs text-red-100 max-w-xl leading-relaxed">
        Tingkatkan status akun Anda menjadi Mitra Penolong agar dapat mempublikasikan posko, ambulans, atau dapur umum yang bisa diakses langsung oleh warga.
      </p>
    </div>
    <a href="/auth/register-partner" class="bg-amber-400 hover:bg-amber-500 text-gray-950 font-black text-xs px-5 py-3 rounded-xl transition shadow-sm whitespace-nowrap block text-center">
      Ajukan Jadi Mitra Penolong ↗
    </a>
  </div>
</div>
