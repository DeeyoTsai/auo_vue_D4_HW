<script setup>
import {ref, reactive} from "vue"

const item = ref('');
const itemArray = reactive([]);
// const toggle = ref(false)

const addItem = () => {
    if (item.value !== ""){
    const item_obj = {
        title:item.value,
        toggle:false,
    };
    
    itemArray.unshift(item_obj);
    item.value = "";
    };
};

const removeItem = (id) => {
    const index = itemArray.findIndex((item) => {
        return item === id;
    })
    itemArray.splice(index,1);
}


</script>

<template>

<header class="m-2">
    <h1 class="text-6xl font-thin select-none">TODO!</h1>
    <div class="font-semibold select-none text-neutral-600">simple and studid todo app</div>
  </header>
  <form class="px-10 py-12 bg-white shadow-sm">
    <section id="app" class="flex">
        <input v-model="item" type="text" placeholder="做點重要的事吧..." class="w-full text-2xl focus:outline-none input-lg input input-bordered" />
        <button v-on:click.prevent="addItem" class="text-xl btn-lg btn btn-neutral">新增</button>
        <!-- <h1>{{ itemArray }}</h1> -->
    </section>
  </form>

  <section class="px-10 py-6 mt-4 bg-white">
    <ul class="">
      <li v-for="it in itemArray" class="flex items-center justify-between py-6 border-b">
        <div class="flex items-center gap-3">
          <input v-model="it.toggle" type="checkbox" id="todo_id_1" class="checkbox" />
          <label v-if="it.toggle" for="todo_id_1" class="text-xl cursor-pointer" style="text-decoration:line-through">
            {{ it.title }}
          </label>
          <label v-else for="todo_id_1" class="text-xl cursor-pointer">
            {{ it.title }}
          </label>
        </div>
        <div>
          <button @click="removeItem(item)" class="p-2 hover:text-white hover:bg-neutral">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M14.74 9l-.346 9m-4.788 0L9.26 9m9.968-3.21c.342.052.682.107 1.022.166m-1.022-.165L18.16 19.673a2.25 2.25 0 01-2.244 2.077H8.084a2.25 2.25 0 01-2.244-2.077L4.772 5.79m14.456 0a48.108 48.108 0 00-3.478-.397m-12 .562c.34-.059.68-.114 1.022-.165m0 0a48.11 48.11 0 013.478-.397m7.5 0v-.916c0-1.18-.91-2.164-2.09-2.201a51.964 51.964 0 00-3.32 0c-1.18.037-2.09 1.022-2.09 2.201v.916m7.5 0a48.667 48.667 0 00-7.5 0"
              />
            </svg>
          </button>
        </div>
      </li>

    </ul>
  </section>
</template>

<style scoped>

</style>
