<script>
    const technologies = [
      { name: 'SvelteKit', emoji: '🚀' },
      { name: 'Tailwind CSS', emoji: '🎨' },
      { name: 'DaisyUI', emoji: '🌼' },
      { name: 'Local Storage', emoji: '💾' },
      { name: 'Svelte Toast', emoji: '🍞' }
    ];
  </script>
  
  <div class="bg-base-200 p-6 rounded-lg shadow-lg">
    <h2 class="text-2xl font-bold mb-4">📚 Project ReadMe</h2>
    <p class="mb-4">This Todo App is built with the following technologies:</p>
    <ul class="space-y-2">
      {#each technologies as tech}
        <li class="flex items-center">
          <span class="text-2xl mr-2">{tech.emoji}</span>
          <span>{tech.name}</span>
        </li>
      {/each}
    </ul>
    <p class="mt-4 text-sm">
      Built with ❤️ using modern web technologies
    </p>
  </div>