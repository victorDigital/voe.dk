<script>
	import Button from '$lib/components/ui/button/button.svelte';
	import Separator from '$lib/components/ui/separator/separator.svelte';
	import * as Breadcrumb from '$lib/components/ui/breadcrumb/index';
	import MapPinHouse from 'lucide-svelte/icons/map-pin-house';
	import BriefcaseBusiness from 'lucide-svelte/icons/briefcase-business';
	import GraduationCap from 'lucide-svelte/icons/graduation-cap';
	import Brain from 'lucide-svelte/icons/brain';
	import TentTree from 'lucide-svelte/icons/tent-tree';
	import Dumbbell from 'lucide-svelte/icons/dumbbell';
</script>

<div class="m-2 w-fit">
	<Breadcrumb.Root>
		<Breadcrumb.List>
			<Breadcrumb.Item>
				<Breadcrumb.Link href="/">Home</Breadcrumb.Link>
			</Breadcrumb.Item>
		</Breadcrumb.List>
	</Breadcrumb.Root>
</div>
<Separator orientation="horizontal"></Separator>
<enhanced:img
	src="/static/home.png"
	alt="landing cover img"
	class="w-full bg-cover vt-name-[cover-img]"
/>
<Separator orientation="horizontal" class="mb-4"></Separator>
<div class="w-full vt-name-[main-content]">
	<span class="mx-4 font-mono text-xs text-muted-foreground">MY MISSION</span>
	<h1 class="px-4 font-zen text-4xl font-black text-white">Building the Websites of Tomorrow</h1>
	<Separator orientation="horizontal" class="mt-4"></Separator>
	<div class="flex w-full">
		<Button class="w-full rounded-none font-zen" variant="default" href="/projects">Projects</Button
		>
		<Button class="w-full rounded-none font-zen" variant="secondary" href="/contact">Contact</Button
		>
	</div>
	<Separator orientation="horizontal" class="mb-4"></Separator>
	<div class="px-4">
		<span class="font-mono text-xs text-muted-foreground">ABOUT ME</span>
		<h2 class="font-zen text-2xl">Hi, I'm Victor</h2>
		<p class="flex items-start *:h-[1em] *:min-w-[24px]">
			<MapPinHouse class="mr-2 mt-1" /> Copenhagen based software engineer
		</p>
		<p class="flex items-start *:h-[1em] *:min-w-[24px]">
			<BriefcaseBusiness class="mr-2 mt-1" /> Currently working as an IT consultant
		</p>
		<p class="flex items-start *:h-[1em] *:min-w-[24px]">
			<GraduationCap class="mr-2 mt-1" /> Pursuing a degree in Computer Science
		</p>
		<p class="flex items-start *:h-[1em] *:min-w-[24px]">
			<Brain class="mr-2 mt-1" /> A decade of experience in software development
		</p>
		<p class="flex items-start *:h-[1em] *:min-w-[24px]">
			<TentTree class="mr-2 mt-1" /> Avid outdoor enthusiast
		</p>
		<p class="flex items-start *:h-[1em] *:min-w-[24px]">
			<Dumbbell class="mr-2 mt-1" /> Loves working out
		</p>
	</div>
	<Separator orientation="horizontal" class="my-4"></Separator>
	<div class="flex items-center justify-between px-4">
		<h2 class="font-zen text-2xl">CV</h2>
		<Button variant="ghost" href="/cv.pdf" target="_blank">View</Button>
	</div>
	<Separator orientation="horizontal" class="my-4"></Separator>
	<p class="text-center">More coming soon</p>
</div>
