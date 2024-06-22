<script lang="ts">
  import dayjs from "dayjs";
  import "dayjs/locale/ar";

  dayjs.locale("ar");

  let time = dayjs().format("A") == "ص" ? "صباح" : "مساء";
</script>

<div class="p-16">
  <header class="flex justify-between">
    <div>
      <h1 class="text-3xl mb-2">{time} الخير👋</h1>
      <h2 class="text-xl text-surface-900/50">
        {dayjs().format("اليوم, dddd D MMMM YYYY")}
      </h2>
    </div>
    <div class="bg-white w-32 h-12 rounded-xl"></div>
  </header>
</div>
