<template>
  <div class="modal">
    <div class="modal-content">
      <!-- เนื้อหาของ modal ไปที่นี่ -->
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalPopup',
};
</script>

<style scoped>
.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #F2F2F2;
  padding: 20px;
  z-index: 9999;
  border-radius: 10px; /* เพิ่มขอบโค้งให้กับกรอบสี่เหลี่ยม */
  max-width: 80%; /* กำหนดความกว้างสูงสุดของ popup */
  max-height: 80%; /* กำหนดความสูงสูงสุดของ popup */
  overflow: auto; /* แสดง scrollbar เมื่อข้อความยาวเกินขนาด popup */
  border: 2px solid #000; /* เพิ่มเส้นกรอบด้วยสีดำ */
}
.modal-content {
  text-align: center;
}


</style>