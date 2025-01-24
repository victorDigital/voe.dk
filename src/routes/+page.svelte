<script>
	import Button from '$lib/components/ui/button/button.svelte';
	import Separator from '$lib/components/ui/separator/separator.svelte';
	import * as Breadcrumb from '$lib/components/ui/breadcrumb/index';
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
	<h1 class="px-4 font-zen text-5xl font-black text-white">
		Hey! Let's Create a Web That Inspires
	</h1>
	<Separator orientation="horizontal" class="mt-4"></Separator>
	<div class="flex w-full">
		<Button class="w-full rounded-none font-zen" variant="default" href="/projects">Projects</Button
		>
		<Button class="w-full rounded-none font-zen" variant="secondary" href="/contact">Contact</Button
		>
	</div>
	<Separator orientation="horizontal" class="mb-4"></Separator>
	<div class="px-4">
		<h2 class="font-zen text-2xl">Hi there 👋</h2>
		<p>
			I'm a web developer who is passionate about creating user-friendly and modern websites. I have
			experience with a wide range of technologies and I am always ready to learn new things. I have
			over 3 years of experience teaching technology, math and programming to young people and
			therefore have a good understanding of communicating complex topics in an easy-to-understand
			way. As well as several years of professional experience with web development, SEO and many
			other technologies.
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
