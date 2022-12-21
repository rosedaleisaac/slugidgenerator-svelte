<style>
  h1 {
    text-align: center;
    color: #333;
  }

  h2 {
    text-align: center;
  }

  textarea {
    width: 80%;
    height: 300px;
    margin: 32px auto;
    padding: 16px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 16px;
    resize: none;
  }

  button {
    display: inline-block;
    margin: 16px 8px;
    padding: 8px 16px;
    border: none;
    border-radius: 4px;
    background-color: #333;
    color: #fff;
    font-size: 16px;
    cursor: pointer;
    box-shadow: 2px 2px 2px rgba(0, 0, 0, 0.2);
  }
</style>

<script>
  import { onMount } from 'svelte';
  import slugid from 'slugid';

  let slugIDs = '';

  const generateSlugIDs = async (count) => {
    const generatedSlugIDs = await Promise.all([...Array(count)].map(() => slugid.nice()));
    slugIDs = generatedSlugIDs.join('\n');
  }
</script>

<h1>SlugID Generator</h1>

<h2>
  SlugIDs are base64 encoded UUIDs that are 22 characters long and safe to use in URLs.
</h2>

<h2>
  <strong>Click the buttons below to generate SlugIDs.</strong>
</h2>

<textarea bind:value={slugIDs} readonly></textarea>

<div style="text-align: center;">
  <button on:click={() => generateSlugIDs(10)}>Generate 10 slugIDs</button>
  <button on:click={() => generateSlugIDs(1)}>Generate 1 slugID</button>
</div>
