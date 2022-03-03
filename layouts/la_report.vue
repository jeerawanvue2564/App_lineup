<template>
  <v-app>
    <div class="bg darken-2 text-center">
      <v-row>
        <v-col>
          <v-app-bar
            absolute
            color="#2978B5"
          >
            <div class="title">
              <v-toolbar-title> รายงานผลการเข้าแถว </v-toolbar-title>
            </div>
          </v-app-bar>
          <!-- -------------------------app-bar------------------------- -->
          <nuxt />
        </v-col>
      </v-row>
      <v-row>
        <v-bottom-navigation
          :value="value"
          grow
          absolute
          background-color="#2978B5"
          color="#ffff"
        >
          <a href="/homepage" style="text-decoration: none;"><v-btn>
            <span style="color: aliceblue;">หน้าหลัก</span>

            <v-icon style="color: aliceblue;">mdi-home-circle</v-icon>
          </v-btn>
          </a>

          <a href="/profile" style="text-decoration: none;"><v-btn>
            <span style="color: aliceblue;">โปรไฟล์</span>

            <v-icon style="color: aliceblue;">mdi-account-circle</v-icon>
          </v-btn>
          </a>
        </v-bottom-navigation>
      </v-row>
    </div>
  </v-app>
</template>

<script>
export default {
  data: () => ({ value: 1 })
}
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Thai&display=swap');
.bgcard{
    background-color: rgb(128, 118, 224);
}
.title{
    color: azure;
    margin-left:10rem;
    font-family: 'IBM Plex Sans Thai', sans-serif;
}
.ft{
    width: 50rem;
    background-color:#4B6587 ;
}

</style>
