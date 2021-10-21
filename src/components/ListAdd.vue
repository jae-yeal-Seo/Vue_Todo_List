<template>
<div>
<v-textarea
          outlined
          v-model="memo"
          label="Outlined textarea"
          value=""
        ></v-textarea> 
        
<v-btn @click="listAdd">

</v-btn>
           
</div>
</template>
<script>

export default{
  data(){
      return {
          memo:null
      }
  },
  methods:{
      listAdd(){
         if(this.memo === null){
             alert('먼저 할 일을 입력하세요');
         } else{
             this.$emit("listAdd",this.memo);
         }
      }
  }
}
</script>
