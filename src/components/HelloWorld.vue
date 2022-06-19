<template>
  <div class="hello">
    <h1>{{ todayDate.toDateString() }}</h1>
    <h2>
      Chinese: Tanggal {{ chineseDate.day }} Bulan {{ chineseDate.month }}
    </h2>

    <input type="date" v-model="selectedDate" />
    <button @click="selectDate()">Select</button>
    <h2 v-if="selectChineseDate">
      Chinese: Tanggal {{ selectChineseDate.day }} Bulan
      {{ selectChineseDate.month }}
    </h2>
  </div>
</template>

<script>
import { CalendarChinese } from 'date-chinese';
const calendarChinese = new CalendarChinese();

export default {
  data() {
    return {
      todayDate: new Date(),
      chineseDate: calendarChinese.fromDate(new Date()),
      selectedDate: null,
      selectChineseDate: null,
    };
  },

  created() {
    this.todayDate = new Date();
    this.chineseDate = calendarChinese.fromDate(this.todayDate);
  },

  methods: {
    selectDate() {
      this.selectChineseDate = calendarChinese.fromDate(
        new Date(this.selectedDate)
      );
    },
  },

  computed: {
    // chineseDate() {
    //   return calendarChinese.fromDate(this.todayDate);
    // },
    // selectChineseDate() {
    //   return calendarChinese.fromDate(new Date(this.selectedDate));
    // },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
