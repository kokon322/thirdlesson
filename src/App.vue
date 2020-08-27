<template>
  <div>
  <h1>ToDoList</h1>  
    <ul>
      <li v-for="(item, i) in toDoList" :key="i">
        {{item}}------- {{i}}<button @click='submitData(item , i )'>SubmitData</button>
        
        <button @click='deleteData(i)'>DeleteData</button>
      </li>
          
    </ul>
     
  </div>
</template>

<script>


export default {
  name: 'App',

  data(){
    return{
         toDoList: [
         'Прокинутися о 8:00',
         'Прийняти душ',
         'Почистити зуби',
         'Одягнутись',
         'Піти на роботу'],
         
    }
  },

  methods:{
    submitData(item , i ){
    this.$http.post('https://lesson----vue.firebaseio.com/todo.json', {item, id: i})
   },
    deleteData(i){
      this.$http.get(`https://lesson----vue.firebaseio.com/todo/${i}.json`, i)
      .then((res)=>{
        console.log(res)
      }) 
    }
    }

 
  
}
</script>

<style>

</style>
