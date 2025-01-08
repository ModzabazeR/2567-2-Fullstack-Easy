<script lang="ts">
  import { cn } from "$lib/utils";

  export let containerClass: string = "";
  export let imgClass: string = "";
  export let picture: string;
  export let text: string | null = null;
</script>

<div
  class="flex flex-col gap-y-2 text-center"
  on:click
  on:keydown={(e) =>
    e.key === "Enter" && e.target && (e.target as HTMLElement).click()}
  role="button"
  tabindex="0"
>
  <div
    class={cn(
      "flex justify-center items-center bg-white aspect-square p-8 rounded-3xl hover:shadow-xl cursor-pointer transition-all",
      containerClass
    )}
  >
    <img
      src={picture}
      alt="card"
      class={cn("w-full h-32 rounded-lg object-cover", imgClass)}
    />
  </div>
  {#if text}
    <p class="text-lg">{text}</p>
  {/if}
</div>
