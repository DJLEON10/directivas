 <script setup>
import { ref } from 'vue';

let newtask = ref('')
let taskList=ref([{
  name:'estdiar',
 done:true
},{
  name:'comer',
 done:false
},
{
  name:'dormir',
 done:false
},


])
function setDone(index){
  taskList.value[index].done =true
}






function addtask(){
  if(newtask.value.trim()=== '') return
  taskList.value.push({
    name:newtask.value,
    done : false })
  newtask.value = '';
}

</script>

<template>
<div class="contenedor">
<h1>Lista de tareas</h1>
<p class="subtitle">{{newtask}}</p>
<div>
  <div class="task" :class="{done : task.done}" v-for="(task, index ) in taskList"  :key="index" >{{task.name}} <span @click="setDone(index)" class="button">x</span></div>

</div>
<input v-model="newtask" @keypress.enter="addtask" placeholder="Escriba su tarea" type="text">
<p v-show="newtask != ''" class="help">presiona enter para agregar la tarea</p>
</div>


</template>

<style scoped>
.done{
  text-decoration: line-through;
}
.help{
  margin: 0;
  font-size: 8px;
  opacity: 0.6;


}
.button{
background-color: #731702;
display: inline-block;
padding: 0 6px;
border-radius: 3px;
}
.button:hover{
  cursor: pointer;
}
.contenedor{
  color: white;
  font-family: 'Dancing Script', cursive;
  background-color: #014040;
  border-radius: 10px;
  max-width: 420px;
  margin: 0 auto;
  padding: 6px 12px;
}
h1{
  text-transform: uppercase;
  font-size: 20px;
  text-align: center;
  margin: 0;
  margin-top: 12px;
}
.subtitle{
  font-size: 10px;
  margin: 0;
  margin-bottom: 16px;
  text-align: center;
  opacity: 0.6;
}
.task{
  background-color: #02735E;
  border-radius: 3px;
  margin-bottom: 1px;
  padding: 2px 2px 1px 6px;
  display: flex;
  justify-content: space-between;
}
.task:hover{
  background-color: #03A678 ;
}
input{
  border: none;
  border-radius: 3px;
  padding: 2px 6px;
  outline: none;
  /*width: calc(100% - 12px) ;*/
  box-sizing: border-box;
  width: 100%;
  margin-top: 12px;
}
input::placeholder{
  opacity: 0.4;
}
</style>
