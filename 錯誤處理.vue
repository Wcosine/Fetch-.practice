<script setup>
  import { ref, onMounted } from 'vue'
  const message = ref('')

  onMounted( async() => {
    try{ 
      // try...catch...
      const res = await fetch('http://localhost:3000/posts');
      // const res = await fetch('https://jsonplaceholder.typicode.com/invalid-url')
      // 如果res用此項, 因無法成功獲得資料, 會得到 "取得資料失敗： Failed to fetch"的值
      
      if(!res.ok){ 
        // 判斷資料取得
        throw new Error(` 錯誤代碼: ${res.status} `) 
        // 錯誤則丟出不繼續執行
      }
      
      const data = await res.json(); 
      // 轉換資料
      message.value = data
      // 輸出資料
      
    } catch(err) { 
      // err是throw丟出來的資料, catch會自動帶入
      message.value = `取得資料錯誤: ${ err.message }` 
      // 輸出資料
      // err.message 會帶入從throw取得的`錯誤狀態碼: $(res.status)`
    }
      // 補充:
      // -.message (錯誤的訊息,會顯示我丟出來的內容)
      // -.name (錯誤的類型名稱):
      //   Error(一般錯誤)、TypeError(型別錯誤)、ReferenceError(找不到變數的錯誤)、SyntaxError(語法錯誤)、RangeError(數字範圍錯誤)
      // -.stack (呼叫過的函式路徑清單,會把在錯誤發生之前的經過都交代一次)
  })
</script>
<template>
  <h1> {{ message }} </h1>
  <!-- 因為message為一陣列, 要先用message[0]選取指定的index, 加上.title(或其他值)可以帶出資料的值 -->
</template>
