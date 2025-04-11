<script lang="ts">
	import Separator from '$lib/components/ui/separator/separator.svelte';
	import type { PageData } from './$types';
	import * as Breadcrumb from '$lib/components/ui/breadcrumb/index.js';
	import Slash from 'lucide-svelte/icons/slash';
	import { cn } from '$lib/utils';

	/* 	import PageHead from '$lib/components/PageHead.svelte';
	import ArticleTitle from '$lib/components/ArticleTitle.svelte';
	import ArticleMeta from '$lib/components/ArticleMeta.svelte'; */

	let { data }: { data: PageData } = $props();

	type C = $$Generic<typeof SvelteComponentTyped<any, any, any>>;
	let component = $derived(data.component) as unknown as C;

	let crumbs: { href: string; label: string }[] = $derived(
		JSON.parse(JSON.stringify(data.frontmatter.crumbs))
	);

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

<svelte:head>
	<title>{data.frontmatter.title} // {data.frontmatter.description}</title>
</svelte:head>

<!-- <PageHead title={data.frontmatter.title} description={data.frontmatter.description} />
<ArticleTitle title={data.frontmatter.title} />
<ArticleMeta author={data.frontmatter.author} date={data.frontmatter.date} /> -->
<div class="m-2 w-fit">
	<Breadcrumb.Root>
		<Breadcrumb.List>
			<Breadcrumb.Item>
				<Breadcrumb.Link href="/">Home</Breadcrumb.Link>
			</Breadcrumb.Item>
			<Breadcrumb.Separator>
				<Slash />
			</Breadcrumb.Separator>
			{#each crumbs as crumb, i}
				<Breadcrumb.Item>
					<Breadcrumb.Link href={crumb.href}>{crumb.label}</Breadcrumb.Link>
				</Breadcrumb.Item>
				{#if i < crumbs.length - 1}
					<Breadcrumb.Separator>
						<Slash />
					</Breadcrumb.Separator>
				{/if}
			{/each}
		</Breadcrumb.List>
	</Breadcrumb.Root>
</div>
<Separator></Separator>
<div class="relative aspect-video overflow-hidden">
	<div class="z-20 p-2 sm:p-3 md:p-4">
		<h1
			class={cn(
				'vt-name-[cover-title] font-zen text-xl font-black sm:text-2xl md:text-5xl',
				data.frontmatter.title_black ? 'text-black' : 'text-white'
			)}
		>
			{data.frontmatter.title}
		</h1>
		<Separator
			orientation="horizontal"
			class={cn(
				'vt-name-[cover-separator] mt-0.5 w-1/2 sm:mt-1 md:mt-2',
				data.frontmatter.title_black ? 'bg-black' : 'bg-white'
			)}
		></Separator>
		<p
			class={cn(
				'vt-name-[cover-desc] font-zen text-sm sm:text-lg md:text-xl',
				data.frontmatter.title_black ? 'text-black' : 'text-white'
			)}
		>
			{data.frontmatter.description}
		</p>
	</div>
	<div class="vt-name-[cover-img] absolute top-0 -z-20 aspect-video w-full overflow-hidden">
		<enhanced:img
			src={imageModules[data.frontmatter.img_src].default}
			alt="landing cover img"
			class="w-full object-cover"
		/>
	</div>
</div>

<article
	class="vt-name-[main-content] prose prose-zinc prose-invert mb-96 w-full max-w-full py-4 text-lg *:mx-2 prose-headings:font-zen prose-pre:mx-0 prose-pre:rounded-none prose-pre:border-b-[1px] prose-pre:border-t-[1px]"
>
	{@render component()}
</article>

<div class="vt-name-[by-line]">
	<Separator></Separator>
	<!-- by line -->
	<div class="flex items-center justify-between px-4 py-2">
		<p class="text-sm text-muted-foreground">
			{data.frontmatter.author} - {data.frontmatter.date}
		</p>
	</div>
</div>

<style>
	@keyframes fade-in {
		from {
			opacity: 0;
		}
	}

	@keyframes fade-out {
		to {
			opacity: 0;
		}
	}

	/* View transitions removed */
</style>
