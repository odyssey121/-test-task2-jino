<template>
  <div class="wrapper">
    <div class="main">
      <div class="text">Для подтеверждения вашего аккаунта вам нужно заполнить все поля, подтвердить
        <br>почтовый ящик и телефон, а также загрузить сканы ваших документов.
        <div class="upload">
          <div id="upload-container">
              <input @change="upload" id="file-input" type="file" name="file" multiple>
              <label for="file-input">
                <div class="upload-image">
                  <img src="../image/upload.svg" alt>
                </div>
              </label>
          </div>
          <div class="upload-text">
            <strong>Загрезите скан страницы с фотографией</strong>
            <p>Размер файла не более 5Мб</p>
          </div>
        </div>
        <div v-for="(file,index) in files" :key="index">
          <wait v-show="file.processing"
          :file="file.name"/>
          <loaded v-show="!file.processing"
          :file="file.name" />

        
      </div>
    </div>
  </div>
  </div>
</template>

<script>
// @ is an alias to /src
import wait from "../components/wait.vue";
import loaded from "../components/loaded.vue";
import shortid from "shortid";
import { close } from 'fs';

export default {
  props:{
  
  },
  components:{
    wait,
    loaded,
  },
  name: 'Task2',
  data () {
    return {
      files:[],
      processing:true,
    	
    }
  },
  methods:{
  	upload(e){
        const id = shortid();
        const filename = e.target.files[0].name;
        const size = `${e.target.files[0].size} Кб`;
        this.files.push({
          id,
          'name':filename,
          'size':size,
          'processing':true,
          'accepted': Math.round(Math.random() * 11) < 5 ? true : false,
        });
        setTimeout(() => {
          this.load(id);
        }, 4000);
    },
    load(id){
      this.files.forEach(file => {
        if(file.id === id)  {file.processing = false;}
      });
    }
  },
  
}
</script>

<style lang="css" scoped>
.text {
  margin-left: 100px;
}
#upload-container input[type="file"] {
  width: 0.1px;
  height: 0.1px;
  opacity: 0;
  position: absolute;
  z-index: -10;
}
.wrapper {
  max-width: 1091px;
  min-width: 819px;
  margin-left: auto;
  margin-right: auto;
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-gap: 12px;
  background: burlywood;
}
.main {
  grid-column: 1/13;
}
.upload {
  margin-top: 15px;
  display: flex;
}
strong {
  border-bottom: 2px solid black;
  margin-top: 2px;
}
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
#upload-container label:hover {
  cursor: pointer;
  text-decoration: underline;
}
</style>