<template>
  <div 
    @dragenter.prevent="toggleActive" 
    @dragleave.prevent="toggleActive" 
    @dragover.prevent
    @drop.prevent
    :class="{'active-dropzone' : active}"
    class="dropzone"
  >
  <span>Drop mp3 File</span>
  <span>OR</span>
  <label class = "file-button" for="dropzoneFile">Select File</label>
  <input type="file" id="dropzoneFile" class="dropzoneFile"/>
  </div>
</template>

<script>
import {ref} from 'vue';
export default {
  name: 'DropZone',
  setup(){
    const active = ref (false);

    const toggleActive = () =>{
      active.value = !active.value;
    }
    /* ส่งไฟล์ไปให้ Back ประมวลผล */
    return {active, toggleActive};
  },
}
</script>


<style scoped lang="scss">
.dropzone{
  width: 600px;
  height: 300px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  row-gap: 25px;
  border: 2px dashed #00b205;
  background-color: #fff;
  transition: .3s ease all;
  border-radius: 25px;
  font-size: 20px;
  

  label{
    padding: 8px 12px;
    color: #fff;
    background-color: #00b205;
    transition: .3s ease all;
  }
  
  input{
    display: none;
  }
}

.active-dropzone{
  color:#fff;
  border-color: #fff;
  background-color: #00b205;
  

  label{
    background-color: #fff;
    color: #00b205;
  }
}
.file-button {
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 22px;
    margin-top: 20px;
    color:#fff;
    border-color: #fff;
    background-color: #00b205;

    label{
      background-color: #fff;
      color: #00b205;
    }
  }
</style>
