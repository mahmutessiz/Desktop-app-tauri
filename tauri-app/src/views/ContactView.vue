<script setup>
import { getClient, ResponseType } from "@tauri-apps/api/http";
import { onMounted, ref } from "vue";

const apiRoute = import.meta.env.VITE_APP_ROUTE;
const apiKey = import.meta.env.VITE_APP_API_KEY;
const margaritas = ref([]);
onMounted(async () => {
  console.log(apiKey, apiRoute, import.meta.env.VITE_APP_FULL);

  const client = await getClient();
  const response = await client.get(
    `${apiRoute}/${apiKey}/search.php?s=margarita`,
    {
      timeout: 30,
      // the expected response type
      responseType: ResponseType.JSON,
    }
  );
  margaritas.value = response.data;
  console.log(response.data);
});
</script>
<template>
  <ul class="w-full flex flex-wrap gap-4 justify-center items-center">
    <li
      v-for="item in margaritas.drinks"
      :key="item"
      class="flex flex-wrap gap-4 justify-center items-center"
    >
      <div>
        {{ item.strDrink }}
        <img :src="item.strDrinkThumb" alt="" class="w-60" />
      </div>
    </li>
  </ul>
  <div class="py-4 text-white">
    <div class="container mx-auto my-12 flex flex-col md:my-36 md:flex-row">
      <div class="flex w-full flex-col p-8 lg:w-2/5">
        <p
          class="my-4 text-3xl leading-relaxed text-yellow-500 md:text-5xl md:leading-snug"
        >
          Contact our team
        </p>
        <p class="my-2 font-sans text-sm text-black md:my-4 md:text-lg">
          <svg
            class="mr-2 inline-block fill-current"
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
          >
            <path
              d="M12 0c-4.198 0-8 3.403-8 7.602 0 4.198 3.469 9.21 8 16.398 4.531-7.188 8-12.2 8-16.398 0-4.199-3.801-7.602-8-7.602zm0 11c-1.657 0-3-1.343-3-3s1.343-3 3-3 3 1.343 3 3-1.343 3-3 3z"
            /></svg
          >Guru Nank Dev Engineering College, Ludhiana
        </p>
        <p class="my-2 font-sans text-sm text-black md:my-4 md:text-lg">
          <svg
            class="mr-2 inline-block fill-current"
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
          >
            <path
              d="M12 12.713l-11.985-9.713h23.971l-11.986 9.713zm-5.425-1.822l-6.575-5.329v12.501l6.575-7.172zm10.85 0l6.575 7.172v-12.501l-6.575 5.329zm-1.557 1.261l-3.868 3.135-3.868-3.135-8.11 8.848h23.956l-8.11-8.848z"
            />
          </svg>
          techfestgndec@gmail.com
        </p>
        <p class="my-2 font-sans text-sm text-black md:my-4 md:text-lg">
          <svg
            class="mr-2 inline-block fill-current"
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
          >
            <path
              d="M20 22.621l-3.521-6.795c-.008.004-1.974.97-2.064 1.011-2.24 1.086-6.799-7.82-4.609-8.994l2.083-1.026-3.493-6.817-2.106 1.039c-7.202 3.755 4.233 25.982 11.6 22.615.121-.055 2.102-1.029 2.11-1.033z"
            /></svg
          >+91745435433
        </p>
        <br />
        <br />
        <p class="my-2 font-sans text-sm text-black md:my-4 md:text-lg">
          Press the chat icon at the right bottom corner to have a live chat
          with our team.
        </p>
      </div>
      <div class="flex w-full flex-col justify-center lg:-mt-12 lg:w-3/5">
        <div class="container">
          <div class="relative flex w-full min-w-0 flex-col break-words">
            <div class="flex-auto p-5 lg:p-10">
              <img
                src="https://user-images.githubusercontent.com/54521023/152731049-cc744a56-1d6f-4945-9566-0fa3b7ad1d24.png"
                alt="contact image"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
