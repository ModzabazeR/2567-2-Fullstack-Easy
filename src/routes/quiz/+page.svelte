<script lang="ts">
  import Card from "$lib/components/card.svelte";
  import { ChevronLeft, ChevronRight } from "lucide-svelte";
  import Input from "$lib/components/ui/input/input.svelte";
  import { Button } from "$lib/components/ui/button";

  let step = 1;
  let appGender: string;
  let appAge: number;
  let appWeight: number;
  let appDrinkingWater: number;

  const genderHandler = (gender: "male" | "female") => {
    appGender = gender;
    step++;
  };

  const ageHandler = () => {
    if (!appAge) {
      alert("กรุณากรอกอายุของคุณ");
      return;
    }

    if (appAge <= 0 || appAge >= 120) {
      alert("กรุณากรอกอายุให้ถูกต้อง");
      return;
    }

    step++;
  };

  const weightHandler = () => {
    if (!appWeight) {
      alert("กรุณากรอกน้ำหนักของคุณ");
      return;
    }

    if (appWeight <= 0 || appWeight >= 300) {
      alert("กรุณากรอกน้ำหนักให้ถูกต้อง");
      return;
    }

    step++;
  };
</script>

<main
  class="bg-[#B4E2FF] h-dvh w-full flex flex-col gap-y-14 justify-center items-center"
>
  {#if step > 1 && step <= 4}
    <button
      class="bg-white rounded-full p-2 hover:shadow-lg fixed top-1/2 left-8 transition-all"
      on:click={() => step--}
    >
      <ChevronLeft class="w-8 h-8" />
    </button>
  {/if}
  

  {#if step === 1}
    <h1 class="font-bold text-4xl">เพศของคุณ</h1>
    <div class="flex gap-16">
      <Card picture="/male.png" on:click={() => genderHandler("male")} />
      <Card picture="/female.png" on:click={() => genderHandler("female")} />
    </div>
  {/if}

  {#if step === 2}
    <h1 class="font-bold text-4xl">อายุของคุณ</h1>
    <Input class="w-24 h-24 text-center !text-3xl font-bold" type="number" bind:value={appAge} placeholder="20" />
    <Button on:click={ageHandler}>ตกลง</Button>
  {/if}

  {#if step === 3}
    <h1 class="font-bold text-4xl">น้ำหนักของคุณ (กก.)</h1>
    <Input class="w-24 h-24 text-center !text-3xl font-bold" type="number" bind:value={appWeight} placeholder="40" />
    <Button on:click={weightHandler}>ตกลง</Button>
  {/if}

  {#if step === 4}
    <h1 class="font-bold text-4xl">ปริมาณน้ำที่ดื่มต่อวัน</h1>
    <div class="grid grid-cols-3 gap-4">
      <Card picture="/1-bottle.png" text="1 ขวด" containerClass="p-4" imgClass="h-8" />
      <Card picture="/2-bottle.png" text="2 ขวด" />
      <Card picture="/3-bottle.png" text="3 ขวด" />
      <Card picture="/4-bottle.png" text="4-5 ขวด" />
      <Card picture="/6-bottle.png" text="6-7 ขวด" />
      <Card picture="/7-bottle.png" text="มากกว่า 7 ขวด" />
    </div>
  {/if}
</main>
