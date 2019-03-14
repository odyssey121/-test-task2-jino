<template>
  <div  class="processing upload">
        <div class="upload-image">
              <img src="../image/wait.svg" alt>
        </div>
        <div class="upload-text">
          <strong>{{file}}</strong>
          <p>Пожалуйста подождите, идёт загрузка....</p>

        </div>
  </div>    
  
</template>

<script>
export default {
  name: "wait",
  props:{
      file:{
          
          default:{},
          required:false,
      }
  },
  
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="css">


.upload-text {
  margin-left: 20px;
}
.upload-image {
  margin-top: 6px;
  width: 50px;
  height: 50px;
  background: white;
  text-align: center;
}
.upload {
  margin-top: 15px;
  display: flex;
}

</style>
