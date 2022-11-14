
<script>
    // We import our page components (similar to the one above).
    import create from "./create.svelte";
    import host from "./host.svelte";
    const pages = [create, host];
    var s = '!"#$%&\'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\\]^_`abcdefghijklmnopqrstuvwxyz{|}~'
    // The current page of our form.
    let page = 0;

    // The state of all of our pages
    let pagesState = [];

    // Our handlers
    function back() {
        page = 0;
    }

    function genserver(questions) {
        pagesState[page] = questions;
        pagesState = pagesState; // Triggering update
        page = 1;
    }
</script>

<h1>bonkers</h1>

<h3>{s}</h3>

<svelte:head>
	<title>bonkers</title>
	<meta name="robots" content="noindex nofollow" />
	<html lang="en" />
</svelte:head>

<!-- We display the current step here -->
<svelte:component
    this={pages[page]}
    {back}
    {genserver}
    initialValues={pagesState[page]}
/>
