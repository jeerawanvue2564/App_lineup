<template>
  <div class="text-center">
    <div class="text-center">
      <v-dialog
        v-model="dialog"
        width="500"
      >
        <v-card>
          <v-card-title class="text-h5 blue lighten-2 ">
            Status Login{{ fname }}
          </v-card-title>

          <v-card-text>
            SUCCESS LOGIN
          </v-card-text>
        </v-card>
      </v-dialog>
    </div>
    <div class="text-center">
      <v-dialog
        v-model="dialog_false"
        width="300"
      >
        <v-card>
          <v-card-title class="text-h5 red lighten-2 ">
            Status Login
          </v-card-title>

          <v-card-text>
            LOGIN ERROR
          </v-card-text>

          <v-divider />

          <v-card-actions>
            <v-spacer />
            <v-btn
              color="primary"
              text
              @click="dialog_false = false"
            >
              Cancel
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </div>
    <v-row justify="center" align="center">
      <div>
        <img
          height="130"
          width="130"
          src="222.png"
          style="margin-top: 60px;"
        >
      </div>
    </v-row>
    <h2 style="margin-top:30px;">
      กิจกรรมเข้าแถวหน้าเสาธง
    </h2>
    <p style="font-size:21px; color: #0061A8">
      วิทยาลัยเทคนิคชัยภูมิ
    </p>

    <div>
      <v-form>
        <v-container>
          <v-row>
            <v-text-field
              v-model="username"
              label="Username or Email"
              outlined
              style="padding: 50px 20px 0px 20px;  "
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
            @click="onSave"
          >
            login
          </v-btn>
          <br>  <a href="/signup">sign up</a>
        </v-container>
      </v-form>
    </div>
    <div>
      <img
        height="200"
        width="200"
        src="555.png"
        style="margin-top: -1rem;"
      >
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    username: '',
    passwd: '',
    dialog: false,
    dialog_false: false
  }),
  methods: {
    async onSave () {
      console.log('onSave')
      // console.log('user:', this.username)
      // console.log('pass:', this.passwd)
      const res = await fetch('http://localhost:7001/login?username=' +
      this.username + '&passwd=' + this.passwd)
      const result = await res.json()

      // const data = await res.json()
      try {
        // console.log('data=', result.data)
        if (result.status === 1) {
          console.log('Login ok')
          this.dialog = true
          setInterval(() => {
            this.dialog = false
            this.$router.push('/homepage')
          }, 1000)
        } else {
          this.dialog_false = true
          setInterval(() => {
            this.dialog_false = false
            this.$router.push('/login')
          }, 1000)
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
p{
  font-family: 'Prompt', sans-serif;
}

.v-text-field--outlined fieldset{
 border-radius: 50px;
 background: #0061A8;
}

.v-text-field--solo{
  border-radius: 30px;
}
</style>
