<script>
	// import successkid from 'images/successkid.jpg';
	const title = "test d'entree texte";
	let text = [];
	let value = "";
	let addText = "";
	let fonts = [];
	let style = "";
	let font = "";
	let fontButtons = [
		{ font: "bold", label: "gras", isChecked: false },
		{ font: "italic", label: "italique", isChecked: false },
		{ font: "underlined", label: "souligné", isChecked: false },
	];
	function addFontStyle(fnt) {
		fonts = [...fonts, fnt];
		return "checked", fonts;
	}
	function newText() {
		addText = value;
		fonts = [...fonts, font];
		style = fonts.join(" ");
		text = [...text, { content: addText, style }];
		console.log(text);
		value = "";
		return text, style;
	}
	$: console.log(font);

	// $: console.log(text);
</script>

<svelte:head>
	<title>{title}</title>
</svelte:head>

<h1>{title}</h1>

<form on:submit|preventDefault={newText}>
	<textarea bind:value cols="100" placeholder="entrez votre texte ici" />
	<!-- <select for="fonts">
		<option name="fonts" type="checkbox" bind:value={font}>
	</label> -->
	<h3>Format du texte</h3>
	{#each fontButtons as button}
		<button
			on:click={() => (button.isChecked = !button.isChecked)}
			class="btn {button.isChecked
				? addFontStyle(button.font)
				: 'unchecked'}">{button.label}</button
		>
	{/each}
	<!-- <select for="fonts">
		<option name="normal">normal</option>
		<option name="bold">gras</option>
		<option name="underlined">souligné</option>
		<option name="italic">italique</option>
	</select> -->
	<br />
	<button type="submit">entrer</button>
</form>
<!-- <p>{addText}</p> -->
<!-- <p>{font}</p> -->
{#each text as entry}
	<div class={entry.style}>{entry.content}</div>
{/each}
<!-- 
<figure>
	<img alt="Success Kid" src="{successkid}">
	<figcaption>Have fun with Sapper!</figcaption>
</figure> -->

<!-- <p><strong>Try editing this file (src/routes/index.svelte) to test live reloading.</strong></p> -->
<style>
	h1,
	figure,
	p {
		text-align: center;
		margin: 0 auto;
	}

	h1 {
		font-size: 2.8em;
		text-transform: uppercase;
		font-weight: 700;
		margin: 0 0 0.5em 0;
	}

	figure {
		margin: 0 0 1em 0;
	}

	img {
		width: 100%;
		max-width: 400px;
		margin: 0 0 1em 0;
	}

	p {
		margin: 1em auto;
	}
	.btn {
		border: none;
		border-radius: 7px;
		min-width: 10rem;
		/* background: goldenrod; */
	}
	.btn:selected,
	.checked {
		background: yellowgreen;
	}
	.unchecked {
		background: goldenrod;
	}
	.bold {
		font-weight: bold;
	}
	.underlined {
		text-decoration: underlined;
	}
	.italic {
		font-style: italic;
	}

	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}
</style>
