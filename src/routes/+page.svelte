<script lang="ts">
  import { MetaTags } from 'svelte-meta-tags';
  import { posts } from '$lib/post';
  import config from '$lib/config';
</script>

<MetaTags
  title={config.name}
  description={config.description}
  canonical={config.url}
  openGraph={{
    url: config.url,
    title: config.name,
    description: config.description,
    siteName: config.name,
  }}
  twitter={{
    handle: '@RangHo_777',
    cardType: 'summary',
    title: config.name,
    description: config.description,
  }}
/>

<h1>take a look at my thoughts</h1>

<ul>
  {#each posts as post}
    <li>
      <a href="/{post.slug}">
        {post.metadata.title}
      </a>
    </li>
  {/each}
</ul>
