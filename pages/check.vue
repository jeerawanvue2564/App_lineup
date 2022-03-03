<template>
  <div class="rounded-xl  text-center">
    <v-row>
      <v-col>
        <div class="btn1">
          <v-autocomplete
            v-model="value"
            :items="week"
            dense
            filled
            label="เลือกวัน"
            solo
            light
            style="height:50px; width:100px;"
            background-color="#7d9ecaa6"
          />
        </div>
      </v-col>
      <v-col>
        <div class="calendar">
          <v-menu
            ref="menu"
            v-model="menu"
            :close-on-content-click="false"
            :return-value.sync="date"
            transition="scale-transition"
            offset-y
            min-width="auto"
          >
            <template #activator="{ on, attrs }">
              <v-text-field
                v-model="date"
                light
                label="วัน/เดือน/ปี"
                prepend-icon="mdi-calendar"
                readonly
                v-bind="attrs"
                v-on="on"
              />
            </template>
            <v-date-picker
              v-model="date"
              no-title
              scrollable
            >
              <v-spacer />
              <v-btn
                text
                color="primary"
                @click="menu = false"
              >
                Cancel
              </v-btn>
              <v-btn
                text
                color="primary"
                @click="$refs.menu.save(date)"
              >
                OK
              </v-btn>
            </v-date-picker>
          </v-menu>
        </div>
      </v-col>
    </v-row>

    <div class="txt01">
      <v-responsive
        class="overflow-y-auto"
        max-height="470"
      >
        <!-- ---------------------------ตาราง-------------------------- -->
        <v-simple-table light>
          <thead>
            <tr style="background: #bdd4ffc2 ;">
              <th class="text-center">
                ชื่อ-นามสกุล
              </th>
              <th class="text-center">
                สถานะ
              </th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="st in student"
              :key="st.student_id"
              class="text-left"
            >
              <td> {{ st.std_name }} {{ st.std_lastname }} </td>
              <!-- --------------------คลิกมา-------------- -->
              <v-radio-group
                v-model="study"
                row
                solo
                dense
                filled
              >
                <td>
                  <v-radio
                    label="มา"
                    color="info"
                    value="1"
                    style="font-size: 12px;"
                  />
                </td>
                <!-- --------------------คลิกขาด-------------- -->
                <td>
                  <v-radio
                    label="ขาด"
                    color="red"
                    value="0"
                  />
                </td>
                <!-- --------------------คลิกสาย-------------- -->
                <td>
                  <v-radio
                    label="สาย"
                    color="primary"
                    value="3"
                  />
                </td>
              </v-radio-group>
            </tr>
          </tbody>
        </v-simple-table>
      </v-responsive>
      <!----ปุ่ม ถอดไป----->
      <div class="next">
        <v-btn
          class="next_bt"
          style="height:40px; width:100px;"
          color="#4ba56d"
        >
          <span class="per" style="color:#e6e6e6; font-size: 19px;">บันทึก</span>
        </v-btn>
      </div>
      <!----------->
    </div>
  </div>
</template>
<script>
export default {
  layout: 'la_check',
  data () {
    return {
      student: [
        { student_id: '1', std_name: 'อธิวัฒน์', std_lastname: 'ทาวรรณ์' },
        { student_id: '2', std_name: 'จีรวรรณ', std_lastname: 'ละลี' },
        { student_id: '3', std_name: 'นรีรัตน์', std_lastname: 'คงสตรี' },
        { student_id: '4', std_name: 'ธีรพงษ์', std_lastname: 'เตจาหลวง' },
        { student_id: '5', std_name: 'สุภาพร', std_lastname: 'เอสันเทียะ' },
        { student_id: '6', std_name: 'ณัฐนิชา', std_lastname: 'วีรคม' },
        { student_id: '7', std_name: 'ปนัสยา', std_lastname: 'จงหมายกลาง' },
        { student_id: '8', std_name: 'พันธกานต์', std_lastname: 'มนัสศิล' },
        { student_id: '9', std_name: 'ปนัดดา', std_lastname: 'จุนทะ' }
      ],
      items: [
        { title: 'Click Me' },
        { title: 'Click Me' },
        { title: 'Click Me' },
        { title: 'Click Me' }
      ],
      week: ['จันทร์', 'อังคาร', 'พุธ', 'พฤหัสบดี', 'ศุกร์'],
      value: null
    }
  },
  computed: {
    upperName () {
      return this.name.toUpperCase()
    }
  },
  created () {
    this.Show()
  },
  methods: {
    async Show () {
      console.log('show data')
      const res = await fetch('http://localhost:7001/list_class')
      const data = await res.json()
      this.student = data.row
      console.log(data.row)
    }
  },
  edit (rid) {
    console.log('rid=', rid)
    this.$router.push('edit_std?rid=' + rid)
  }
}

</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Thai&display=swap');
.bg{
    background: #f6f2e0 ;
}
.txt01{
    color: black;
}
.rounded-xl{
    padding-top: 4rem;
}
.calendar{
  padding-top: -4rem;
  margin-left: -6rem;
}
.btn1{
  margin-left: 5px;
  margin-top: 8px;
}
.next{
  margin-top: 15px;
  margin-bottom: 4rem;
}
</style>
