<script>
  import { getContext } from "svelte";
  import Context from "../context";

  const { hide } = getContext(Context.Modal)

  let count = 0
  const clicks = 5
  $: if (count === clicks) hide()
  $: remaining = clicks - count

  function increment() {
    count++
  }
</script>

<style>
  div {
    padding: 40px;
    background-color: var(--purple);
    color: white;
    font-family: var(--font-sans);
    font-weight: bold;
    text-align: center;
    user-select: none;
    font-size: 20px;
  }
  div:hover {
    cursor: pointer;
  }
</style>

<div on:click={increment}>
  Click me {remaining} more time{remaining === 1 ? "" : "s"} to close this modal!
</div>
