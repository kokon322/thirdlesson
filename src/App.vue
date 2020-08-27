<template>
  <div>
  <h1>ToDoList</h1>  
  <input type="text" v-model="scaner.scan">
  <button @click="addToData">addToData</button>


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
    
  }
    
  }

 
  
}
</script>

<style>

</style>
