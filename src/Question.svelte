<script> 
    import Draggable from "./Draggable.svelte";
    import { questions } from './questions'
    export let x = "";
    export let y = "";
    export let o1 = "";
    export let o2 = "";
    export let o3 = "";
    export let o4 = "";
    export let index;
    var visible = true;
    function onSubmit() {
        questions[index.id] = {question: x, answer: y, option1: o1, option2: o2, option3: o3, option4: o4}
        console.log(questions)
    }
</script>

<Draggable>
    {#if visible}

    <form on:submit|preventDefault={onSubmit}>        
        <label for="question">Question</label>
        <input bind:value={x} id="question" name="question" />
        <br/>
        <br/>

        <label for="input">Answer </label>
        <input bind:value={y} id="input" name="input" />
        <br/>
        <br/>
        <label class="option" for="option">Option 1 </label>
        <input class="option" bind:value={o1} id="option" name="option" />
        <br/>
        <br/>
        <label class="option" for="option">Option 2 </label>
        <input class="option" bind:value={o2} id="option" name="option" />
        <br/>
        <br/>
        <label class="option" for="option">Option 3 </label>
        <input class="option" bind:value={o3} id="option" name="option" />
        <br/>
        <br/>
        <label class="option" for="option">Option 4 </label>
        <input class="option" bind:value={o4} id="option" name="option" />

        <br/>
        <br/>
        <button type="submit">Add Question/Submit</button>

    </form>
    <button class="x_button" on:click={() => {
        questions.slice(index, 1);
        visible = false;
    }}>x</button>
    {/if}
    <br/>
    <button class="hide" on:click={() => {
        visible = !visible;
    }}>Hide</button>
</Draggable>
