<script lang="ts">
  let { article = {
    slug: 'detail',
    title: 'Judul Artikel Edukasi',
    summary: 'Tidak ada ringkasan artikel.',
    readTime: '3 min baca',
    category: 'Edukasi'
  } } = $props();
</script>

<div class="bg-white rounded-2xl border border-gray-100 shadow-sm hover:shadow-md transition overflow-hidden flex flex-col justify-between group">
  <div class="h-44 bg-gray-100 relative flex items-center justify-center overflow-hidden">
    <div class="text-center p-4 space-y-1">
      <div class="w-12 h-12 mx-auto rounded-xl bg-purple-50 text-purple-600 flex items-center justify-center text-2xl font-bold">📖</div>
      <span class="text-[10px] text-gray-400 font-medium block">Info Darurat Edukasi</span>
    </div>
    <span class="absolute top-3 left-3 bg-white/90 backdrop-blur-md text-purple-700 font-bold text-[10px] px-2.5 py-1 rounded-lg border border-purple-100 shadow-sm">{article.category}</span>
  </div>
  <div class="p-5 space-y-2 flex-1 flex flex-col justify-between">
    <div class="space-y-1.5">
      <div class="flex items-center justify-between text-[11px] text-gray-400"><span>⏱️ {article.readTime}</span><span>Terbaru</span></div>
      <h3 class="font-bold text-sm text-gray-900 group-hover:text-purple-600 transition line-clamp-2">{article.title}</h3>
      <p class="text-xs text-gray-500 line-clamp-3 leading-relaxed">{article.summary}</p>
    </div>
    <div class="pt-3 border-t border-gray-100 flex items-center justify-between">
      <a href="/blog/{article.slug}" class="text-xs font-bold text-purple-600 hover:underline flex items-center gap-1"> Baca Selengkapnya ➔ </a>
    </div>
  </div>
</div>
