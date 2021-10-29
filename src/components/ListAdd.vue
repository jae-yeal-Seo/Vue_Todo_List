<template>
<div>
<v-textarea
          outlined
          v-model="memo"
          label="Outlined textarea"
          value=""
        ></v-textarea> 
        
<v-btn @click="listAdd">리스트 추가</v-btn>
<v-btn @click="listEdit">리스트 수정</v-btn>
           
</div>
</template>
<script>
import { eventBus } from "../main"

export default{
  data(){
      return {
          memo:null,
          index:null
      }
  },
  methods:{
      listAdd(){
         if(this.memo === null){
             alert('먼저 할 일을 입력하세요');
         } else{
             this.$emit("listAdd",this.memo);
         }
         this.memo = null
      },
      listEdit(){
           if(this.memo === null){
             alert('먼저 할 일을 입력하세요');
         } else{
             this.$emit("listEdit",this.memo, this.index);
         }
         this.memo = null
      }
  },
  created(){
      //eventBus는 듣고 있다가 List에서 listEdit을 발생시키면 두번째 인자를 실행시킨다.
      eventBus.$on('listEdit',(memo,index)=>{
          this.memo = memo;
          this.index = index;
      })
  }
}
</script>
