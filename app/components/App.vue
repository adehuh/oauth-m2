<template>
  <Page actionBarHidden="true" >
    <AbsoluteLayout ref="containerView">
     
      <login-oauth2 left="10" top="2"></login-oauth2>
      
    </AbsoluteLayout>
  </Page>
</template>

<script lang="ts">
import LoginOauth2 from "@/components/core/LoginOauth2.vue";
import axios from 'axios/dist/axios';
export default {
  components: {
    
    
    LoginOauth2
  },
  mounted(){
  setTimeout(() => {
         
        }, 350);
  },
  updated: function () {
    
 },
  data() {
    return {
      msg: "Hello World!",
      isRightSliderShow:false,
      screenWidth:0
    };
  },
  methods:{
        

        
  }
};
</script>

<style scoped>
ActionBar {
  background-color: #53ba82;
  color: #ffffff;
}

.message {
  vertical-align: center;
  text-align: center;
  font-size: 20;
  color: #333333;
}
</style>
