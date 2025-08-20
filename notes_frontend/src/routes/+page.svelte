<script lang="ts">
  import NoteList from '$lib/components/NoteList.svelte';
  import NoteEditor from '$lib/components/NoteEditor.svelte';
  import { notes, selectedId, selectedNote, selectNote, deleteNote } from '$lib/notesStore';

  // Using auto-subscription for Svelte stores
  $: allNotes = $notes;
  $: currentId = $selectedId;
  $: current = $selectedNote;

  function onSelect(id: string) {
    selectNote(id);
  }

  function onDelete(id: string) {
    if (confirm('Delete this note? This action cannot be undone.')) {
      deleteNote(id);
    }
  }
</script>

<svelte:head>
  <title>Simple Notes</title>
  <meta name="description" content="Create, edit, and manage notes in your browser." />
</svelte:head>

<NoteList notes={allNotes} selectedId={currentId} onSelect={onSelect} onDelete={onDelete} />
<NoteEditor note={current} />
