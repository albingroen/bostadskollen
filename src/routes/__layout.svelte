<script lang="ts">
	import '../styles/tailwind-output.css';
	import splitbee from '@splitbee/web';

	splitbee.init();

	const url = 'https://bostadskollen.albingroen.com';
	const image =
		'https://res.cloudinary.com/albin-groen/image/upload/q_auto,f_auto/v1639560937/bostadskollen-seo_vndez1.png';
	const description =
		'Med Bostadskollen kan du ta reda på vad en bostadsrätt egentligen skulle kosta dig varje månad.';
	const title = 'Bostadskollen - Vad kostar det egentligen?';
</script>

<svelte:head>
	<title>{title}</title>
	<meta name="title" content={title} />
	<meta name="description" content={description} />

	<meta property="og:type" content="website" />
	<meta property="og:url" content={url} />
	<meta property="og:title" content={title} />
	<meta property="og:description" content={description} />
	<meta property="og:image" content={image} />

	<meta property="twitter:card" content="summary_large_image" />
	<meta property="twitter:url" content={url} />
	<meta property="twitter:title" content={title} />
	<meta property="twitter:description" content={description} />
	<meta property="twitter:image" content={image} />
</svelte:head>

<main class="antialiased">
	<slot />
</main>
