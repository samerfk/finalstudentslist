<template>
    <div>
        
            <div v-for="mystudent in mystudents" v-bind:key="mystudent.id">
                <h3>
                    <span v-bind:class="{'line-through':mystudent.graduated}">
                        {{mystudent.name}} 
                    </span>
                
                    <input type="button" value="x" class="del" v-on:click="$emit('del-student', mystudent.id)" />
                    &nbsp;&nbsp;&nbsp;
                    <input type="button" value="Toggle" class="toggle" v-on:click="mystudent.graduated = !mystudent.graduated" />
                </h3>
        
                
            </div>
        
    </div>
</template>
<script>
export default {
    name:"Students",
    props:["mystudents"],

}
</script>
<style scoped>
.del{
    
    color:black;
    font-size: larger;
    width: 40px;
    background-color: red;
    border:2px solid black;
    position: relative;
    height:40px;
    border-radius:40%;
    cursor:pointer;
    text-align: center;
}
.line-through{
    text-decoration: line-through;
    font-size: larger;
}

.toggle{
    color:black;
    width:40x;
    height:40px;
    background-color:green;
    cursor:pointer;
    text-align: center;
    border-radius:40%;
    font-size: larger;

}

</style>