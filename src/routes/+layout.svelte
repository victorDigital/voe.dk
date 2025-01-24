<script lang="ts">
	import Button from '$lib/components/ui/button/button.svelte';
	import Separator from '$lib/components/ui/separator/separator.svelte';
	import '../app.css';
	let { children } = $props();

	import { onNavigate } from '$app/navigation';

	onNavigate((navigation) => {
		if (!document.startViewTransition) return;

		return new Promise((resolve) => {
			document.startViewTransition(async () => {
				resolve();
				await navigation.complete;
			});
		});
	});
</script>

<header class="py-4 vt-name-[header]">
	<div class="mx-auto flex w-full max-w-6xl items-center justify-between px-4 font-zen">
		<Button variant="ghost" href="/">
			<img src="/logo_white.svg" alt="logo" class="w-16" />
		</Button>
		<div class="flex flex-row items-center gap-4">
			<Button variant="ghost" href="/projects">Projects</Button>
			<Button variant="ghost" href="/contact">Contact</Button>
		</div>
	</div>
</header>
<Separator orientation="horizontal"></Separator>
<div class="mx-auto flex w-full max-w-3xl flex-row">
	<Separator orientation="vertical"></Separator>
	<main class="min-h-screen w-full max-w-3xl">
		{@render children()}
	</main>
	<Separator orientation="vertical"></Separator>
</div>
<footer class="text-center text-sm text-muted-foreground vt-name-[footer]">
	<Separator orientation="horizontal"></Separator>
	<div
		class="h-6 w-full overflow-hidden bg-[image:repeating-linear-gradient(315deg,_hsl(var(--border))_0,_hsl(var(--border))_1px,_transparent_0,_transparent_50%)] bg-[size:10px_10px] md:h-4 xl:h-3"
	></div>
	<Separator orientation="horizontal"></Separator>
	<section class="my-4 flex justify-center gap-2">
		<img src="/logo_white.svg" alt="logo" class="w-16" />
	</section>
	<section class="my-4 flex justify-center gap-4 font-zen">
		<a href="/contact"> Contact </a>
		<a href="/projects"> Projects </a>
	</section>
</footer>

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

	@keyframes slide-from-top {
		from {
			transform: translateY(-30px);
		}
	}

	@keyframes slide-to-bottom {
		to {
			transform: translateY(30px);
		}
	}

	::view-transition-old(main-content) {
		animation:
			90ms cubic-bezier(0.4, 0, 1, 1) both fade-out,
			300ms cubic-bezier(0.4, 0, 0.2, 1) both slide-to-bottom;
	}

	::view-transition-new(main-content) {
		animation:
			210ms cubic-bezier(0, 0, 0.2, 1) 90ms both fade-in,
			300ms cubic-bezier(0.4, 0, 0.2, 1) both slide-from-top;
	}
</style>
