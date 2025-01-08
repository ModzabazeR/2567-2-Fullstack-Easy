<script lang="ts">
  import Button from "$lib/components/ui/button/button.svelte";
  import { ArrowRight } from "lucide-svelte";
</script>

<main
  class="h-dvh w-full flex flex-col gap-y-4 justify-center items-center text-center p-2 overflow-hidden"
>
  <div class="flex flex-col gap-y-4 relative">
    <img
      src="/water-kun.png"
      alt="water-kun"
      class="block md:hidden w-40 mx-auto"
    />
    <h1 class="text-2xl md:text-4xl text-white font-bold drop-shadow-lg">
      วันนี้คุณดื่มน้ำแล้วหรือยัง?
    </h1>
    <p class="text-white drop-shadow-md">
      ไม่แน่ใจว่าตัวเองดื่มน้ำพอหรือยังเหรอ? ลองทำแบบทดสอบของเราสิ!
    </p>
    <a href="/quiz">
      <Button
        class="bg-white text-black hover:bg-slate-300 hover:text-gray-900 text-center h-max"
      >
        <ArrowRight class="w-6 h-6 mr-2" />
        ไปทำความรู้จักตัวเองกันเลย!
      </Button>
    </a>
    <!-- align 0,0 to the end, end position of its relative parent -->
    <img
      src="/water-kun.png"
      alt="water-kun"
      class="hidden md:block w-40 absolute bottom-0 right-0 translate-x-[60%] translate-y-[60%]"
    />
  </div>
  <div class="h-full w-full bg-blue-500/50 absolute -z-10"></div>
  <div
    class="h-full w-full absolute bg-[url(https://static.vecteezy.com/system/resources/previews/007/412/629/large_2x/water-splash-background-free-vector.jpg)] bg-cover -z-20 bg-top"
  ></div>
</main>
