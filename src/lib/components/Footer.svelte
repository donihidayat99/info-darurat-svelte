<footer class="bg-gray-900 text-gray-300 py-12 border-t border-gray-800">
  <div class="container mx-auto px-4 max-w-7xl grid grid-cols-1 md:grid-cols-4 gap-8 mb-8">
    
    <!-- Kolom 1: Tentang Platform -->
    <div class="space-y-4">
      <div class="flex items-center gap-2">
        <span class="bg-red-600 text-white font-black px-2.5 py-1 rounded text-lg">INFO</span> 
        <span class="text-xl font-bold text-white tracking-tight">DARURAT</span>
      </div> 
      <p class="text-xs text-gray-400 leading-relaxed">Platform direktori digital terbuka untuk mempermudah masyarakat mengakses posko, layanan medis, dan alat darurat secara cepat dan andal.</p> 
      <div class="text-xs text-gray-500"><p>Versi PWA & Akses Offline Siaga.</p></div>
    </div> 

    <!-- Kolom 2: Kategori Layanan -->
    <div>
      <h4 class="text-white font-bold text-sm mb-4">Kategori Layanan</h4> 
      <ul class="space-y-2 text-xs text-gray-400">
        <li><a href="/listings" class="hover:text-red-500 transition">Darurat Medis & Ambulans</a></li> 
        <li><a href="/listings" class="hover:text-red-500 transition">Pemadam Kebakaran</a></li> 
        <li><a href="/listings" class="hover:text-red-500 transition">SAR & Evakuasi Bencana</a></li> 
        <li><a href="/categories" class="hover:text-red-500 transition">Lihat Semua Kategori ↗</a></li>
      </ul>
    </div> 

    <!-- Kolom 3: Tautan Cepat -->
    <div>
      <h4 class="text-white font-bold text-sm mb-4">Tautan Cepat</h4> 
      <ul class="space-y-2 text-xs text-gray-400">
        <li><a href="/" class="hover:text-red-500 transition">Beranda Utama</a></li> 
        <li><a href="/donation" class="hover:text-red-500 transition">Dukung Kami & Donasi</a></li> 
        <li><a href="/blog" class="hover:text-red-500 transition">Artikel & Tips Siaga</a></li> 
        <li><a href="/dashboard" class="hover:text-red-500 transition">Dashboard Akun</a></li>
      </ul>
    </div> 

    <!-- Kolom 4: Buletin / Newsletter -->
    <div>
      <h4 class="text-white font-bold text-sm mb-4">Buletin Darurat</h4> 
      <p class="text-xs text-gray-400 mb-3">Dapatkan informasi pembaharuan posko siaga langsung ke email Anda.</p> 
      <form onsubmit={(e) => { e.preventDefault(); alert('Terima kasih telah berlangganan buletin!'); }} class="space-y-2">
        <input type="email" placeholder="Alamat email Anda..." required class="w-full px-3 py-2 rounded-lg bg-gray-800 border border-gray-700 text-xs text-white focus:outline-none focus:ring-1 focus:ring-red-500"> 
        <button type="submit" class="w-full bg-red-600 hover:bg-red-700 text-white text-xs font-bold py-2 rounded-lg transition cursor-pointer">Berlangganan</button>
      </form>
    </div>

  </div> 

  <!-- Bagian Bawah Footer -->
  <div class="container mx-auto px-4 max-w-7xl pt-6 border-t border-gray-800 flex flex-col sm:flex-row items-center justify-between gap-4 text-xs text-gray-500">
    <p>© 2026 Info Darurat Indonesia. Dibangun untuk kemanusiaan dan kecepatan akses.</p>
    <div class="flex items-center gap-4">
      <a href="/donation" class="hover:text-gray-300 transition">Bantuan Operasional</a>
      <span>•</span>
      <a href="/auth/login" class="hover:text-gray-300 transition">Portal Mitra</a>
    </div>
  </div>
</footer>
