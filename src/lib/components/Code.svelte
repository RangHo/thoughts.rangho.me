<script lang="ts">
  import hljs from 'highlight.js';
  import lightTheme from 'highlight.js/styles/tokyo-night-light.css?inline';
  import darkTheme from 'highlight.js/styles/tokyo-night-dark.css?inline';

  import { colorMode } from '$lib/dark';

  const hljsThemes = {
    light: lightTheme,
    dark: darkTheme,
  };

  export let lang: string;
  export let code: string;
  export let inline = false;

  let highlighted = '';

  $: highlighted = hljs.highlight(code, { language: lang }).value;
</script>

<!-- https://github.com/sveltejs/svelte/issues/5292#issuecomment-787743573 -->
<svelte:head>
  {@html `<${''}style>${hljsThemes[$colorMode]}</${''}style>`}
</svelte:head>

<slot {highlighted}>
  {#if inline}
    <code class="hljs language-{lang} font-monospace">{@html highlighted}</code>
  {:else}
    <pre class="my-4 not-prose"><code class="hljs language-{lang} font-monospace"
        >{@html highlighted}</code
      ></pre>
  {/if}
</slot>
