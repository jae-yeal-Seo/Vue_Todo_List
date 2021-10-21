<template>
<v-container>
  <v-layout row wrap>
    <v-flex xs6 pa-2>
      <List :todoList="todoList" @listDelete="listDelete"
      @statusControl="statusControl"/>
    </v-flex>
    <v-flex xs6 pa-2>
       <ListAdd @listAdd="listAdd" />
    </v-flex>
  </v-layout>

</v-container>
</template>

<script>
import List from './List'
import ListAdd from './ListAdd'
export default {
  data(){
    return {
      todoList:[]
    }
  },
  components:{
    List,
    ListAdd
  },
  methods:{
    listAdd(memo){
      this.todoList.push({ memo:memo, status:"created"})
    },
    statusControl(index,status){
      this.todoList[index].status = status;
    },
    listDelete(index){
      this.todoList.splice(index,1);
    }
  },
  created(){
   
  }
}
</script>