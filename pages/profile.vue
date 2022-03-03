<template>
  <v-container>
    <div class="text-center">
      <div>
        <img
          height="120"
          width="120"
          src="profile.png"
          style="margin-top: 190px;"
        >
      </div>
      <div
        class="text"
        style="text-align: left;"
      >
        <label>ชื่อ : นางสาวจีรวรรณ</label><br>
        <label>นามสกุล : ละลี</label><br>
        <label>เบอร์โทรศัพท์ : 0936952871</label><br>
        <label>ครูประจำชั้น : ปวช.3</label><br>
        <label>แผนก : หัวใจดวงโตๆ</label>
        <v-btn
          class="btn"
          rounded
          color="#F9F871"
          dark
          style="margin-bottom: 4rem;"
        >
          <h3>แก้ไขข้อมูล</h3>
        </v-btn>
      </div>
    </div>
  </v-container>
</template>
<script>
export default {
  layout: 'la_profile'
}
</script>
<style>

@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Thai&display=swap');

.bg {
  background: #eed9c3 ;
}

label{
  font-family: 'IBM Plex Sans Thai', sans-serif;
  font-size: 20px;
  color: #000;
}
.text{
  margin-left: 6rem;
  padding-bottom: 190px;
  padding-top: 30px;
}
h3{
  font-family: 'IBM Plex Sans Thai', sans-serif;
  color: #000;
}

</style>
