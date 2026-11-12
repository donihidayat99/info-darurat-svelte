<script lang="ts">
  import CitizenDashboard from './citizen/+page.svelte';
  import PartnerDashboard from './partner/+page.svelte';
  import AdminDashboard from './admin/+page.svelte';

  let currentRole = $state('citizen');

  let user = {
    name: 'Doni Pratama',
    email: 'doni@example.com',
    roleLabel: 'Warga Terdaftar',
    joinedDate: 'Januari 2026'
  };
</script>

<svelte:head>
  <title>Dashboard Pengguna - Info Darurat</title>
</svelte:head>

<div class="max-w-6xl mx-auto px-4 py-8 space-y-8">
  
  <!-- Bar Simulasi Ganti Role -->
  <div class="bg-amber-50 border border-amber-200 p-4 rounded-2xl flex flex-wrap items-center justify-between gap-4">
    <div class="space-y-0.5">
      <span class="text-xs font-bold text-amber-900 block">🛠️ Mode Simulasi Tampilan Dashboard</span>
      <p class="text-[11px] text-amber-700">Pilih role di bawah untuk melihat perbedaan tampilan dashboard secara modular.</p>
    </div>
    <div class="flex items-center gap-2">
      <button onclick={() => currentRole = 'citizen'} class="px-3 py-1.5 rounded-xl text-xs font-bold transition cursor-pointer {currentRole === 'citizen' ? 'bg-amber-600 text-white shadow-sm' : 'bg-white text-amber-900 border border-amber-300 hover:bg-amber-100'}">
        👤 Warga
      </button>
      <button onclick={() => currentRole = 'partner'} class="px-3 py-1.5 rounded-xl text-xs font-bold transition cursor-pointer {currentRole === 'partner' ? 'bg-amber-600 text-white shadow-sm' : 'bg-white text-amber-900 border border-amber-300 hover:bg-amber-100'}">
        🤝 Mitra Penolong
      </button>
      <button onclick={() => currentRole = 'admin'} class="px-3 py-1.5 rounded-xl text-xs font-bold transition cursor-pointer {currentRole === 'admin' ? 'bg-amber-600 text-white shadow-sm' : 'bg-white text-amber-900 border border-amber-300 hover:bg-amber-100'}">
        🛡️ Admin
      </button>
    </div>
  </div>

  <!-- Header Info Profil Singkat -->
  <div class="bg-white p-6 rounded-2xl border border-gray-100 shadow-sm flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4">
    <div class="flex items-center gap-4">
      <div class="w-14 h-14 rounded-2xl bg-red-600 text-white font-black text-xl flex items-center justify-center shadow-sm">
        {user.name.charAt(0)}
      </div>
      <div class="space-y-1">
        <div class="flex items-center gap-2">
          <h1 class="text-xl font-black text-gray-900 tracking-tight">{user.name}</h1>
          <span class="text-[10px] font-bold px-2.5 py-0.5 rounded-full uppercase tracking-wider {currentRole === 'admin' ? 'bg-purple-100 text-purple-700' : currentRole === 'partner' ? 'bg-green-100 text-green-700' : 'bg-blue-100 text-blue-700'}">
            {currentRole === 'admin' ? 'Administrator' : currentRole === 'partner' ? 'Mitra Penolong' : 'Warga'}
          </span>
        </div>
        <p class="text-xs text-gray-500">{user.email} • Bergabung sejak {user.joinedDate}</p>
      </div>
    </div>
    <button onclick={() => alert('Fitur keluar akun')} class="text-xs font-bold text-red-600 bg-red-50 hover:bg-red-100 px-4 py-2 rounded-xl transition cursor-pointer">
      Keluar Akun
    </button>
  </div>

  <!-- RENDER KOMPONEN BERDASARKAN ROLE -->
  {#if currentRole === 'citizen'}
    <CitizenDashboard {user} />
  {:else if currentRole === 'partner'}
    <PartnerDashboard />
  {:else if currentRole === 'admin'}
    <AdminDashboard />
  {/if}

</div>
