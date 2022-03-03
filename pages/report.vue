<template>
  <div class="rounded-xl  text-center">
    <h3>
      ส่งผลการเข้าแถวระดับ ปวส.2 <br>
      ประจำปีการศึกษาที่ 2/2564
    </h3>
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
                    label="ผ่าน"
                    color="info"
                    value="1"
                    style="font-size: 12px;"
                  />
                </td>
                <!-- --------------------คลิกขาด-------------- -->
                <td>
                  <v-radio
                    label="ไม่ผ่าน"
                    color="red"
                    value="0"
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
          style="height:40px; width:100px; margin-left: 0.5rem; margin-right: 0.5rem;"
          color="#EAB902"
        >
          <span class="per" style="color:#e6e6e6; font-size: 16px;">แก้ไข</span>
        </v-btn>

        <v-btn
          class="next_bt"
          style="height:40px; width:100px; margin-left: 0.5rem; margin-right: 0.5rem;"
          color="#4ba56d"
        >
          <span class="per" style="color:#e6e6e6; font-size: 16px;">ส่งผล</span>
        </v-btn>
      </div>
      <!----------->
    </div>
  </div>
</template>
<script>
export default {
  layout: 'la_report',
  data () {
    return {
      student: [
        { name: 'อธิวัฒน์ ทาวรรณ์' },
        { name: 'จีรวรรณ ละลี' },
        { name: 'นรีรัตน์ คงสตรี' },
        { name: 'ธีรพงษ์ เตจาหลวง' },
        { name: 'สุภาพร เอสันเทียะ' },
        { name: 'ณัฐนิชา วีรคม' },
        { name: 'ปนัสยา จงหมายกลาง' },
        { name: 'พันธกานต์ มนัสศิล' },
        { name: 'ปนัดดา จุนทะ' }
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
h3{
  font-family: 'IBM Plex Sans Thai', sans-serif;
  color: rgb(100, 96, 96);
}
</style>
