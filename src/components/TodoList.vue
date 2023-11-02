<script setup lang="ts">
import {ref} from 'vue'


interface Item{
    name: string
    flag: boolean
}

const tasks = ref<Item[]>([
    
])

const newItemName = ref('')


const addItem = () =>{
    if (newItemName.value!='' ){
        tasks.value.push({name: newItemName.value,flag: false})
        newItemName.value = ''

    }
    
}

function hanten(A: { flag: boolean; }){
    if (A.flag==false){
        A.flag = true
    }else{
        A.flag = false
    }
}
</script>


<template>
  <div>未達成リスト</div>
  <ul>
    <li v-for="task in tasks" :key="task.name" >
        <div v-if="task.flag==false" >タスク名: {{ task.name }}</div>
        <button v-if="task.flag==false" @click="hanten(task)">完了</button>
        
    </li>
  </ul>
  <div>達成リスト</div>
  <ul>
    <li v-for="task in tasks" :key="task.name" >
        <div v-if="task.flag==true" >タスク名: {{ task.name }}</div>
        
    </li>
  </ul>
  <div>
    <label>   
        名前
        <input v-model = "newItemName" type="text" />                                                                                                                                                            
    </label>
    
    <button @click="addItem">追加</button>
  </div>
</template>

<style>
.over500{
    color: red;
}
</style>