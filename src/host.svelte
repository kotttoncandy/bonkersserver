<script>
  export let back;
  import { io } from "socket.io-client";
  export let initialValues;
  import { questions } from './questions'
  console.log(questions)
  const socket = io("localhost:3000");
  let name = "world";
  let x = 0;
  var pos = [
    [
      Math.floor(Math.random() * 1100) + 100,
      Math.floor(Math.random() * 1100) + 100,
    ],
    [
      Math.floor(Math.random() * 1100) + 100,
      Math.floor(Math.random() * 1100) + 100,
    ],
    [
      Math.floor(Math.random() * 1100) + 100,
      Math.floor(Math.random() * 1100) + 100,
    ],
  ];
  let ready = false;
  /*

  var questions = [
    {
      question: "whats 1 + 1?",
      answer: "3",
    },
  ];
    socket.emit("init", {

    })
    */
</script>

<p>Code: {x}</p>

<button
  on:click={() => {
    back();
  }}>Back</button
>

<button
  on:click={() => {
    x = 1;
    //x = Math.floor(Math.random() * 10000000) + 1000000;
    socket.emit("init_room", x);
    ready = true;
  }}
>
  Generate Code!
</button>

{#if ready}
  <button
    on:click={() => {
      //x = Math.floor(Math.random() * 10000000) + 1000000;
      socket.emit("ready", x, questions, pos);
      ready = true;
    }}
  >
    Play! (Wait untill ALL students join)
  </button>
{/if}
