<script setup>
import { onMounted, ref } from 'vue';

const users = ref([]);

onMounted(
// 生命週期 onMounted 在介面完成後先初始化資料等內容
  async()=>{
  // async() 是非同步語法，通常跟await一起使用

     const res =  await fetch('https://jsonplaceholder.typicode.com/users');
     // res = response
     // 用 await 等待資料取得，不然他會直接進行下一步

     const data = await res.json();
     // 因為不是ref('')，所以不用寫成res.value
     // 用json()把取得的資料解析成 JavaScript 可以使用的物件或陣列

    users.value = data
  }
)
</script>

<template>
  <ul>
    <li v-for="user in users" :key="user.id">{{ user.name }}</li>
  </ul>
</template>
