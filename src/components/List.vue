<template>
    <div>
        <v-card 
        class="pa-3"
        :class="{'done': list.status === 'done'}"
        v-for="(list,index) in todoList"
        :key="index"> 
            <p>{{ list.memo }}</p>
            <v-btn
            v-if = "list.status === 'created'"
             @click="$emit('statusControl',index, 'done')" 
             fab flat small color="green">완료</v-btn>
            <v-btn  
           v-else
            @click="$emit('statusControl',index, 'created')" 
            fab flat small color="blue">부활</v-btn>
            <v-btn  
            @click="$emit('listDelete',index)" 
            fab flat small color="red">제거</v-btn>
        </v-card>
        
    </div>
</template>
<script>

export default{
  props :['todoList'],
}
</script>

<style scoped>
.done{
    background-color: rgba(0,0,0,0.1);
}
.done p {
    text-decoration: line-through;
    color: rgba(0,0,0,0.5);
}
</style>