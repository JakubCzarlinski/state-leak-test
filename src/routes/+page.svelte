<script>
  import Component from "$lib/Component.svelte";
  import { mount, unmount } from "svelte";

  let target;

  function generateStatefulComponent() {
    for (let i = 0; i < 100_000; i++) {
      let myInnocentState = $state({text: "hello"})
      const toUnmount = mount(Component, {
          target: target,
          props: myInnocentState,
      });
      unmount(toUnmount);
    }
  }
</script>

<button onclick={generateStatefulComponent}>
  generate of stateful components
</button>

<div bind:this={target}></div>
