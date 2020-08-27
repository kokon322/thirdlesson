<template>
  <div>
  <h1>ToDoList</h1>  
  <input type="text" v-model="scaner.scan">
  <button @click="addToData">addToData</button>
  <button @click="getFromData">GetFromData</button>
  <ul>
    <li v-for="(todo , i) in toDoList" :key="i">
        {{todo.scan}}
    </li>
  </ul>

  </div>
</template>

<script>


export default {
  name: 'App',

  data(){
    return{
    scaner: {scan:''},
    toDoList: [],
         
    }
  },

  methods:{
  addToData(){
    this.$http.post('https://lesson----vue.firebaseio.com/todo.json', this.scaner)
    this.scaner.scan = ''
    },
  getFromData(){
    this.$http.get('https://lesson----vue.firebaseio.com/todo.json')
    .then((res)=>{
      return res.json()
    }).then((res) =>{
       return Object.values(res)    
    }).then((res)=>{
      for(let item of res){
        this.toDoList.push(item)
      }
    })
  }
    
  }

 
  
}
</script>

<style>

</style>
