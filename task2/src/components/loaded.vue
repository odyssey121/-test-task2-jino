<template>
  <div  class="processing upload">
        <div class="upload-image">
              <img src="../image/ok.svg" alt>
        </div>
        <div class="upload-text">
            <strong>Файл загружен</strong>
          <p>{{filename}} , {{size}}</p>
        </div>
        <div class="checking">
            <span v-if="accepted === 'Принято'"
            class="allow"
            > {{status}}</span>
            
            <span v-else-if="accepted === 'Отклонено'"
            class="deny"
            > {{status}}</span>

            <span v-else> {{status}}</span>

        </div>
  </div>    
  
</template>

<script>
export default {
  name: "loaded",
  props:['filename','size','accepted'],
  data () {
    return{
        
    }
  },
  computed: {
    status(){
      return this.accepted;
        
    }
  },
  
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="css">
.checking{
    margin-left: 100px;
    line-height: 68px;
}

.upload-text {
  margin-left: 20px;
  width: 250px;
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
.allow{
  color:green;
  font-weight: 800;
}
.deny{
  color:red;
  font-weight: 800;
}

</style>