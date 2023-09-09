<script setup>
import ToDoItemvue from "@/page/item.vue"
import { ref, reactive, onBeforeMount } from "vue"
import { v4 as uuidv4 } from "uuid"
const title = "AUO"
const ToDoItem = ref("")
const ToDoItems = reactive([])

const addToDoItem = () => {
  if (ToDoItem !== "") {
    const item = {
      id: uuidv4(),
      title: ToDoItem.value,
      checkbox: false,
    }
    ToDoItems.unshift(item)
    ToDoItem.value = ""

  }
}

const removeItem = (id) => {
    console.log('test') 
    
  const index = ToDoItems.findIndex((ToDoItem) => {
    return ToDoItem.id === id
  })

  ToDoItems.splice(index, 1)
}

onBeforeMount(() => {

})


</script>
<template>
<main class="container mx-auto">
      <header class="m-2">
        <h1 class="text-6xl font-thin select-none">TODO!</h1>
        <div class="font-semibold select-none text-neutral-600">simple and studid todo app</div>
      </header>
      <form class="px-10 py-12 bg-white shadow-sm">
        <section class="flex">
          <input
          type="text"
          placeholder="做點重要的事吧..."
          class="w-full text-2xl focus:outline-none input-lg input input-bordered"
          v-model="ToDoItem"
        />
          <button class="text-xl btn-lg btn btn-neutral" @click.prevent="addToDoItem" >新增</button>
        </section>
      </form>
      <section class="px-10 py-6 mt-4 bg-white">
        <ul class="">
            <ToDoItemvue
        @remove-auo-item="removeItem"
        v-for="d in ToDoItems"
        :ToDoItem="d"
      />
          
        </ul>
      </section>
    </main>


</template>

<style scoped></style>
