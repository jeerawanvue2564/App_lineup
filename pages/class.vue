<template>
  <v-container>
    <div>
      <!-- ---------------ปุ่มเช็กชื่อ---------------- -->
      <div class="btt">
        <div class="b_name">
          <v-btn
            class="btn1"
            style="height:90px; width:250px;"
            color="#8AB6D6"
          >
            <span class="txt2" style="color:#030303; font-size: 20px;"> ห้อง E1 </span>
          </v-btn>
        </div>
        <!-- -----------------ปุ่มรายงาน--------------------- -->
        <div class="b_report">
          <v-btn
            class="btn1"
            style="height:90px; width:250px;"
            color="#8AB6D6"
          >
            <span class="txt2" style="color:#030303; font-size: 20px;"> ห้อง E5 </span>
          </v-btn>
        </div>
        <div>
          <img
            height="230"
            width="230"
            src="555.png"
            style="margin-top: 60px;"
          >
        </div>
      </div>
    </div>
  </v-container>
</template>
<script>
export default {
  layout: 'la_class'
}
</script>
<style>

@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Thai&display=swap');

.bg {
  background: #eed9c3 ;
}

.btt{
  padding-top: 10rem;
}
.b_name{
  padding-top: 1rem;
}
.b_report{
  padding-top: 4rem;
}
.txt2{
  font-family: 'IBM Plex Sans Thai', sans-serif;
}
</style>
