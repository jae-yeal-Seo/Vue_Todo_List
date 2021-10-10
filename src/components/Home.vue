<template>
<v-container>
  {{ todoList }}
  <v-layout row wrap>
    <v-flex xs6>
      <List/>
    </v-flex>
    <v-flex xs6>
       <ListAdd @listAdd="listAdd"/>
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
    }
  }
}
</script>