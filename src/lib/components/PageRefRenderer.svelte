<script lang="ts">
	let { href, hideTopBorder } = $props();
	import Separator from './ui/separator/separator.svelte';
	import { onMount } from 'svelte';
	import { slugFromPath } from '$lib/utils';
	import Skeleton from './ui/skeleton/skeleton.svelte';

	let frontmatter: Record<string, any> = $state({});

	let loaded = $state(false);

	onMount(async () => {
		const modules = import.meta.glob('/src/pages/*.{md,svx,svelte.md}');
		for (const [path, resolver] of Object.entries(modules)) {
			if (slugFromPath(path) === href.replaceAll('/', '')) {
				const post = (await resolver()) as { metadata: Record<string, any> };
				frontmatter = post.metadata || {};
				loaded = true;
				break;
			}
		}
	});

	const imageModules: Record<string, { default: string }> = import.meta.glob(
		'/static/*.{avif,gif,heif,jpeg,jpg,png,tiff,webp,svg}',
		{
			eager: true,
			query: {
				enhanced: true
			}
		}
	);
</script>

{#if !hideTopBorder}
	<Separator class="!mx-0 px-0" orientation="horizontal"></Separator>
{/if}
<a
	class="!mx-0 flex h-16 w-full flex-row items-center justify-between overflow-hidden pl-4 font-zen no-underline duration-300 hover:bg-accent md:h-24"
	{href}
	aria-label="Go to page"
>
	{#if loaded}
		<div>
			<p class="m-0 mb-1 line-clamp-1 break-words leading-tight">{frontmatter.title}</p>
			<p class="m-0 line-clamp-1 hidden break-words text-xs opacity-75 md:block">
				{frontmatter.description}
			</p>
		</div>
		<div class="aspect-square h-16 transition-all duration-300 *:my-0 md:aspect-video md:h-24">
			<enhanced:img
				src={imageModules[frontmatter.img_src].default}
				alt="logo"
				class="h-16 object-cover antialiased transition-all duration-300 md:h-24"
			/>
		</div>
	{:else}
		<noscript>
			<div class="w-full">
				<div>
					<p class="m-0 mb-1 line-clamp-1 break-words leading-tight">Visit {href}</p>
					<p class="m-0 line-clamp-1 hidden break-words text-xs opacity-75 md:block">
						This content requires JavaScript to load details
					</p>
				</div>
			</div>
		</noscript>
		<div></div>
		<Skeleton class="aspect-square h-16 *:my-0 md:aspect-video md:h-24"></Skeleton>
	{/if}
</a>
<Separator class="!mx-0 px-0" orientation="horizontal"></Separator>
