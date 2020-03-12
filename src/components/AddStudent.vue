<template>
    <div>
        <form v-on:submit="addStudent">
            <p> Add student:
                <input type="text" v-model="name" />
                <input type="submit" value="Submit" />
            </p>
        </form>
    </div>
</template>
<script>
import { v4 as uuidv4 } from 'uuid';
export default {
    name:"AddStudent",
    data(){
        return{
            name:''
        }
    },
    methods:{
        addStudent(e){
            e.preventDefault(); //form won't submit to file
            let newstudent = {
                id:uuidv4(),
                name: this.name,
                graduated:false
            }

            this.$emit('add-student', newstudent)
        }
    }
}
</script>
<style scoped>
</style>