<script>
// @ts-nocheck
    import {storeFE} from './store'
    $storeFE = []
    import Question from "./Question.svelte";
    export let genserver;
    export let initialValues = [];
    import {questions} from './questions' 
    export var idIncrement = 0
    function  addItem(question, answer) {
        // @ts-ignore
        let l = $storeFE.length;
        $storeFE[l] = { id:idIncrement };
		idIncrement++;	// increment our id to add additional items
        console.log(questions)
    }
</script>

<button
    on:click={() => {
        addItem()
}}>Add More Questions</button
>

<ul>
	{#each $storeFE as item}
			<svelte:component this={Question} index = {item}/>
	{/each}
</ul>


<button on:click={() => {

console.log(questions)
    genserver(questions)
}}>Host</button>