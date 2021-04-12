<script>
	// import successkid from 'images/successkid.jpg';
	const title = "test d'entree texte";
	let text = [];
	let value = "";
	let addText = "";
	let font = "";
	function newText() {
		addText = value;
		text = [...text, addText];
		console.table(text);
		value = "";
		return text;
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
	<!-- <select bind:value={}>
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
	<div>{entry}</div>
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

	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}
</style>
