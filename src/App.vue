<template>
  <div id="app">
    <AddStudent v-on:add-student="addStudent" />
    <Students v-bind:mystudents = "mystudents" v-on:del-student="deleteStudent" />
  </div>
</template>

<script>
import Students from './components/Students.vue'
import AddStudent from './components/AddStudent.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Students, AddStudent
  },
  data(){
    return{
      mystudents : []
    }
  },
  methods:{
    addStudent(newStudent){
      //collection mystudents
      axios.post('https://studentslist-f0d8b.firebaseio.com/mystudents.json', newStudent)
      .then(data => console.log(data))
      .catch(err => console.log(err))

      this.mystudents.push(newStudent);
    },

    deleteStudent(id){
      axios.delete('https://studentslist-f0d8b.firebaseio.com/mystudents/' + id + '.json')

      this.mystudents = this.mystudents.filter(obj => obj.id != id)
    }

  },
  //do the first thing as the application loads
  created(){
    axios.get('https://studentslist-f0d8b.firebaseio.com/mystudents.json')
    .then(data => {
      let temp = [];
      let newdata = data.data;
      for(let key in newdata){
        newdata[key].id  =  key;
        //add each object into a temporary array
        temp.push(newdata[key]);
        //console.log(newdata[key]);
      }
      this.mystudents = temp;

    })
    .catch(err => console.log(err))
  }
}
</script>

<style>
#app {
 
}
</style>
