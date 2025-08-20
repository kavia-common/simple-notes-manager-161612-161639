<script lang="ts">
  import '../app.css';
  import TopBar from '$lib/components/TopBar.svelte';
  import { createNewNote } from '$lib/notesStore';
  let { children } = $props();

  function handleCreate() {
    createNewNote();
  }
</script>

<div class="layout">
  <TopBar onCreate={handleCreate} />
  <main>
    {@render children()}
  </main>
</div>

<style>
  .layout {
    display: grid;
    grid-template-rows: 56px 1fr;
    min-height: 100vh;
    background: var(--color-background);
  }
  main {
    display: grid;
    grid-template-columns: auto 1fr;
    min-height: calc(100vh - 56px);
  }
</style>
