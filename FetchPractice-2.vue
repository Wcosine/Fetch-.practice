<script setup>
  import { ref } from 'vue'
  
  const name = ref('');
  const message = ref('');

  const createUser = async() =>{
    if(!name.value){
      alert('請輸入使用者名稱')
      return
    }
    const res = await fetch ('http://localhost:3000/users', {
      // fetch(url, options),以下都是options,表示這次的請求怎麼送出
      // 用陣列呈現要記得用{}
      
      method: "POST", 
      // 指定使用方式,預設為"GET"
      
      headers: {'Content-Type': 'application/json'},
      // 告訴伺服器這是json格式
      
      body: JSON.stringify({name: name.value}),
      // 告訴伺服器要轉成json字串     
    })
    
      const data = await res.json();
      // 將取得資料(json字串)轉成JS物件
    
      message.value = `使用者 ${data.name} 建立成功, ID: ${data.id}`;
      name.value = '';
  }
</script>

<template>
  <h1>創建使用者ID</h1>
  <input v-model="name" type="text" placeholder="請輸入使用者名稱"/>
  <!-- 用v-model雙向綁定 -->
  
  <button @click="createUser">提交</button>
  <p> {{ message }} </p>
  <!-- message 會自動解套,不用寫成message.value -->
  
</template>
