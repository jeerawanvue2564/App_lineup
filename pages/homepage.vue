<template>
  <v-container>
    <div>
      <!-- ---------------ปุ่มเช็กชื่อ---------------- -->
      <div class="btt">
        <div class="b_name">
          <a href="/week" style="text-decoration: none;"><v-btn
            class="btn1"
            style="height:100px; width:300px;"
            color="#8AB6D6"
          >
            <img
              height="70"
              width="70"
              src="check.png"
              style="margin-top: 4px; margin-left: -110px;"
            >
            <span class="txt2" style="color:#030303; font-size: 20px;"> เช็กชื่อเข้าแถว </span>
          </v-btn></a>
        </div>
        <!-- -----------------ปุ่มผล--------------------- -->
        <div class="b_report">
          <a href="/result" style="text-decoration: none;"> <v-btn
            class="btn1"
            style="height:100px; width:300px;"
            color="#8AB6D6"
          >
            <img
              height="70"
              width="70"
              src="documents.png"
              style="margin-top: 4px; margin-left: -110px;"
            >
            <span class="txt2" style="color:#030303; font-size: 20px; margin-left: 25px;"> ผลการเข้าแถว </span>
          </v-btn></a>
        </div>
        <!-- -------------------ปุ่มส่งรายงานผลกิจกรรม------------------ -->
        <div class="b_pass">
          <a href="/report" style="text-decoration: none;"><v-btn
            class="btn1"
            style="height:100px; width:300px;"
            color="#8AB6D6"
          >
            <img
              height="70"
              width="70"
              src="completed-task.png"
              style="margin-top: 4px; margin-left: -125px;"
            >
            <span class="txt2" style="color:#030303; font-size: 20px; margin-left: 30px;"> รายงานผล </span>
          </v-btn></a>
        </div>
      </div>
    </div>
  </v-container>
</template>
<script>
export default {
  layout: 'la_homepage'
}
</script>
<style>

@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Thai&display=swap');

.bg {
  background: #eed9c3 ;
}

.btt{
  padding-top: 7rem;
}
.b_name{
  padding-top: 1rem;
}
.b_report{
  padding-top: 5rem;
}
.b_pass{
  padding-top: 5rem;
  padding-bottom: 90px;
}
.txt2{
  font-family: 'IBM Plex Sans Thai', sans-serif;
}
</style>
