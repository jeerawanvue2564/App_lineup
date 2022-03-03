<template>
  <div class="rounded-xl  text-center">
    <h3>แผนกเทคโนโลยีสารสนเทศ กลุ่ม E5/2564</h3>
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
                จำนวนมาเข้าแถว
              </th>
              <th class="text-center">
                เปอร์เซ็นต์
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
              <td> 10 </td>
              <td> 60% </td>
            </tr>
          </tbody>
        </v-simple-table>
      </v-responsive>
      <!----ปุ่ม ถอดไป----->
      <div class="next">
        <v-btn
          class="next_bt"
          style="height:40px; width:100px; "
          color="#F4D35D"
        >
          <span class="per" style="color:#292928; font-size: 19px;">กลับ</span>
        </v-btn>
      </div>
      <!----------->
    </div>
  </div>
</template>
<script>
export default {
  layout: 'la_result',
  data () {
    return {
      student: [
        { name: 'อธิวัฒน์ ทาวรรณ์', quantity: '10', percent: '60%' },
        { name: 'จีรวรรณ ละลี', quantity: '10', percent: '60%' },
        { name: 'นรีรัตน์ คงสตรี', quantity: '10', percent: '60%' },
        { name: 'ธีรพงษ์ เตจาหลวง', quantity: '10', percent: '60%' },
        { name: 'สุภาพร เอสันเทียะ', quantity: '10', percent: '60%' },
        { name: 'ณัฐนิชา วีรคม', quantity: '10', percent: '60%' },
        { name: 'ปนัสยา จงหมายกลาง', quantity: '10', percent: '60%' },
        { name: 'พันธกานต์ มนัสศิล', quantity: '10', percent: '60%' },
        { name: 'ปนัดดา จุนทะ', quantity: '10', percent: '60%' }
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
  color: #000;
}
</style>
