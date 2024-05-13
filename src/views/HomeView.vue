<template>
  <div class="home">
    <h1>DropZone</h1>
    <DropZone @drop.prevent="drop" @change="selectedfile"/> 
    <span class="file-info">File: {{dropzoneFile.name }}</span>
    <button class ="next-button" @click="togglePopup">Open Popup</button>
    <!-- ใช้ teleport เพื่อแสดง popup -->
    <teleport to="body">
      <ModalPopup v-if="showPopup">
        <!-- เนื้อหาของ popup ที่คุณต้องการ -->
        <div>
          <h2>Content ของ Popup</h2>
          <p>{{dropzoneFile.name }}</p>

          <button class="close-button" @click="closePopup">Close</button>
        </div>
      </ModalPopup>
    </teleport>
  </div>
</template>

<script>
import DropZone from '@/components/DropZone.vue'
import ModalPopup from '@/components/ModalPopup.vue';
import {ref} from "vue";

export default {
  name: 'HomeView',
  components: {
    DropZone,
    ModalPopup,

  },
    setup(){
    let dropzoneFile = ref ("");
    const showPopup = ref(false);

    const togglePopup = () => {
      showPopup.value = !showPopup.value;
    };

    const closePopup = () => {
      showPopup.value = false;
    };

    const drop = (e) => {
      dropzoneFile.value = e.dataTransfer.files[0]
    };

    const selectedfile = () => {
      dropzoneFile.value = document.querySelector(".dropzoneFile").files[0];
    };

    return { dropzoneFile, drop, selectedfile, showPopup, togglePopup, closePopup};
  },
  
}
</script>

<style lang="scss" scoped>
.home{
  position: relative;
  height: 100vh;
  display: flex;
  flex-direction: column ;
  justify-content: center;
  align-items: center;
  background-color: #F2F2F2;

  h1{
    font-size: 40px;
    margin-bottom: 32px;
    color: #00b205;
  }

  .file-info{
    margin-top: 32px;
  }
  .next-button {
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
    margin-top: 20px;
    color:#fff;
    border-color: #fff;
    background-color: #00b205;

    label{
      background-color: #fff;
      color: #00b205;
    }
  }
  .close-button {
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
  color: #fff;
  background-color: #f44336; /* สีแดงเพื่อปุ่มปิด */
  }

  .close-button:hover {
    background-color: #d32f2f; /* กำหนดสีเมื่อ hover หน้าปุ่ม */
  }
}
</style>