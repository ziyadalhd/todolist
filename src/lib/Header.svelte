<script lang="ts">
  import {
    ListBox,
    ListBoxItem,
    popup,
    type PopupSettings,
  } from "@skeletonlabs/skeleton";
  import dayjs from "dayjs";
  import "dayjs/locale/ar";

  dayjs.locale("ar");

  let time = dayjs().format("A") == "ص" ? "صباح" : "مساء";

  let comboboxValue: string = "جميع المهام";

  $: console.log(comboboxValue);

  const popupCombobox: PopupSettings = {
    event: "click",
    target: "popupCombobox",
    placement: "bottom",
    closeQuery: ".listbox-item",
  };
</script>

<header class="flex justify-between">
  <div class="pb-3">
    <h1 class="text-3xl mb-2">{time} الخير👋</h1>
    <h2 class="text-xl text-surface-900/50">
      {dayjs().format("اليوم, dddd D MMMM YYYY")}
    </h2>
  </div>

  <button
    class="btn variant-filled w-48 h-fit justify-between rounded-xl bg-white text-surface-900"
    use:popup={popupCombobox}
  >
    <span>{comboboxValue}</span>
    <span class="!m-0 variant-ghost-surface rounded-md"
      ><svg
        xmlns="http://www.w3.org/2000/svg"
        class="h-7 w-7"
        viewBox="0 0 24 24"
        ><path
          fill="none"
          stroke="currentColor"
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2.5"
          d="m7 10l5 5m0 0l5-5"
        /></svg
      ></span
    >
  </button>

  <div class="card w-48 shadow-xl py-2" data-popup="popupCombobox">
    <ListBox rounded="rounded-none">
      <ListBoxItem bind:group={comboboxValue} name="medium" value="جميع المهام"
        >جميع المهام</ListBoxItem
      >
      <ListBoxItem bind:group={comboboxValue} name="medium" value="مهام اليوم"
        >مهام اليوم</ListBoxItem
      >
    </ListBox>
    <div class="arrow bg-surface-100-800-token" />
  </div>
</header>
