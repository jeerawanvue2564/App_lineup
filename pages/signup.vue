<template>
  <div class="text-center">
    <v-row justify="center" align="center">
      <div>
        <img
          height="110"
          width="110"
          src="222.png"
          style="margin-top: 40px;"
        >
      </div>
    </v-row>

    <h2 style="margin-top:20px;">
      สมัครสมาชิก
    </h2>
    <p style="font-size:15px; color: #0061A8">
      กิจกรรมเข้าแถวหน้าเสาธง วิทยาลัยเทคนิคชัยภูมิ
    </p>

    <div class="box">
      <v-card
        vlevation="3"
        light
        class="box"
      >
        <div class="box">
          <h4>ลงทะเบียนใช้งาน</h4>

          <v-form>
            <v-container>
              <v-row>
                <v-text-field
                  v-model="fullname"
                  label="ชื่อ นามสกุล"
                  outlined
                  style="padding: 50px 20px 0px 20px;  "
                />
              </v-row>

              <v-row>
                <v-text-field
                  v-model="tel"
                  label="เบอร์โทรศัพท์"
                  outlined
                  style="padding: 0px 20px 0px 20px;  "
                />
              </v-row>

              <v-row>
                <v-text-field
                  v-model="username"
                  label="Username or Email"
                  outlined
                  style="padding: 0px 20px 0px 20px;  "
                />
              </v-row>

              <v-row>
                <v-text-field
                  v-model="class5"
                  label="ครูประจำชั้น"
                  outlined
                  style="padding: 0px 20px 0px 20px;  "
                />
              </v-row>

              <v-row>
                <v-text-field
                  v-model="passwd"
                  label="Password"
                  type="password"
                  outlined
                  style="padding: 0px 20px 0px 20px;"
                  append-icon="mdi-eye-off"
                />
              </v-row>

              <v-btn
                class="btn"
                rounded
                color="primary"
                dark
                @click="Save"
              >
                Signup
              </v-btn>
            </v-container>
          </v-form>

          <div class="text-center">
            <v-dialog
              v-model="dialog"
              width="500"
            >
              <v-card>
                <v-card-title class="text-h5 blue lighten-2">
                  ลงทะเบียนสำเร็จ
                </v-card-title>
              </v-card>
            </v-dialog>
            <div />
          </div>
          <!-- ------------------Status ok ------------------------- -->
          <div class="text-center">
            <v-dialog
              v-model="dialog_false"
              width="500"
            >
              <v-card>
                <v-card-title class="text-h5 red lighten-2 ">
                  ลงทะเบียนไม่สำเร็จ
                </v-card-title>
              </v-card>
            </v-dialog>
          </div>
          <!-- ------------------Status error ------------------------- -->

          <div>
            <p style="color : rgb(0, 0, 0);font-size:15px">
              Already signed up? <a href="/login">Log in</a>
            </p>
          </div>
        </div>
      </v-card>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data: () => ({
    reveal: false,
    fullname: '',
    username: '',
    tel: '',
    passwd: '',
    class5: '',
    dialog: false,
    dialog_false: false
  }),
  methods: {
    clr () {
      this.fullname = ''
      this.username = ''
      this.tel = ''
      this.passwd = ''
      this.class5 = ''
    },
    async Save () {
      const std = {
        fullname: this.fullname,
        username: this.username,
        tel: this.tel,
        passwd: this.passwd,
        class5: this.class5

      }
      console.log('user:', std)
      const res = await axios.post('http://localhost:7001/save', std)
      console.log(res.data)
      try {
        if (res.data.status > 0) {
          console.log('บันทึกสำเร็จ')
          this.dialog = true
          this.clr()
          setInterval(() => {
            this.dialog = false
            this.$router.push('/login')
          }, 3000)
        } else {
          this.dialog_false = true
          this.clr()
          setInterval(() => {
            this.dialog_false = false
            this.$router.push('')
          }, 3000)
        }//  end if
      } catch (error) {
        console.log('Error Login')
      }
    }
  }
}
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Prompt:wght@200&display=swap');

h2{
  color: #0061A8;
  font-family: 'Prompt', sans-serif;
}

h4{
  color: #0061A8;
  font-family: 'Prompt', sans-serif;

}

p{
  font-family: 'Prompt', sans-serif;
}

.box{
  background: #f8dbba6c;

}

.v-text-field--outlined fieldset{
 background: #3fa0e646;
}

</style>
