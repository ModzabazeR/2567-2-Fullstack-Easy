<script lang="ts">
  import { goto } from "$app/navigation";
  import Button from "$lib/components/ui/button/button.svelte";
  import { Share2, Sticker } from "lucide-svelte";
  import { onMount } from "svelte";

  let status: "too-low" | "normal" | "too-high" = "normal";

  onMount(() => {
    const urlParams = new URLSearchParams(window.location.search);
    const suitableAmount = urlParams.get("suit");
    const realAmount = urlParams.get("real");

    if (!suitableAmount || !realAmount) {
      alert("กรุณากรอกข้อมูลให้ครบถ้วน");
      goto("/quiz");
    } else {
      const realAmountNumber = parseInt(realAmount);
      const suitableAmountNumber = parseInt(suitableAmount);
      const result = (realAmountNumber / suitableAmountNumber) * 100;

      if (result < 90) {
        status = "too-low";
      } else if (result > 110) {
        status = "too-high";
      } else {
        status = "normal";
      }
    }
  });
</script>

<main
  class="bg-[#B4E2FF] h-dvh w-full flex justify-center items-center p-8 md:p-20"
>
  <div
    class="flex justify-center items-center flex-col gap-8 bg-white w-full h-full rounded-3xl p-4 md:p-8"
  >
    {#if status === "too-low"}
      <h1 class="text-4xl font-bold text-center">
        คุณดื่มน้ำ<span class="text-red-500">น้อยเกินไป</span>นะ!
      </h1>
      <img src="/too-low.png" alt="too-low" class="w-48" />
      <p class="text-center w-5/6 md:w-4/6">
        ดูเหมือนวันนี้จะดื่มน้ำน้อยไปหน่อยนะ! 😟
        ร่างกายยังไม่ได้รับน้ำที่เพียงพอ
        อาจทำให้รู้สึกเหนื่อยหรือไม่สดชื่นเท่าที่ควร ลองดื่มน้ำสักแก้วตอนนี้นะ
        เพื่อเติมความสดชื่นให้กับตัวเอง! 💧✨
        การดื่มน้ำเป็นสิ่งสำคัญในการดูแลสุขภาพ
        อย่าลืมตั้งเป้าหมายการดื่มน้ำใหม่ๆ และค่อยๆ เพิ่มขึ้นทีละนิดๆ นะ!
      </p>
    {/if}

    {#if status === "normal"}
      <h1 class="text-4xl font-bold text-center">
        คุณดื่มน้ำ<span class="text-green-500">พอดีแล้ว</span>นะ!
      </h1>
      <img src="/just-right.png" alt="just-right" class="w-48" />
      <p class="text-center w-5/6 md:w-4/6">
        เยี่ยมมาก! คุณมีกิจวัตรดื่มน้ำในปริมาณที่เหมาะสม 🥳💧
        ร่างกายได้รับน้ำเพียงพอแล้ว ช่วยให้ระบบต่างๆ ทำงานได้ดี
        และช่วยให้คุณรู้สึกสดชื่นทั้งวัน! ✨ รักษาความสม่ำเสมอนี้ต่อไปนะ
        เพราะสุขภาพที่ดีเริ่มต้นจากการดูแลตัวเองแบบนี้แหละ!
      </p>
    {/if}

    {#if status === "too-high"}
      <h1 class="text-4xl font-bold text-center">
        คุณดื่มน้ำ<span class="text-red-500">มากเกินไป</span>นะ!
      </h1>
      <img src="/too-high.png" alt="too-high" class="w-48" />
      <p class="text-center w-5/6 md:w-4/6">
        โอ๊ะ! คุณอาจดื่มน้ำมากไปหน่อย 😅💦 ถึงแม้การดื่มน้ำจะดีต่อสุขภาพ
        แต่การดื่มน้ำมากเกินไปในครั้งเดียว
        อาจส่งผลต่อสมดุลของเกลือแร่ในร่างกายได้นะ 🧂
        ลองแบ่งดื่มให้เหมาะสมในแต่ละช่วงของวัน
        เพื่อให้ร่างกายได้รับน้ำในปริมาณที่พอดีดีกว่า! 💧✨
      </p>
    {/if}

    <div class="flex gap-8 relative">
      <Button class="border-2 flex gap-2" variant="outline"
        ><Share2 size={16} />แชร์ผลลัพธ์</Button
      >
      <Button class="border-2 flex gap-2" variant="outline"
        ><Sticker size={16} />สมัครสมาชิก</Button
      >
	  <img class="w-72 hidden md:block absolute bottom-0 right-0 translate-x-[100%] translate-y-[30%]" src="/note.png" alt="note">
    </div>
  </div>
</main>
