<template>
  <div class="hello">
    <h1>{{ todayDate.toDateString() }}</h1>
    <h2>
      Chinese: Tanggal {{ chineseDate.day }} Bulan {{ chineseDate.month }}
    </h2>

    <input type="date" v-model="selectedDate">
    <button v-on:click=""> Select </button>
    <h2 v>
      Chinese: Tanggal {{ selectChineseDate.day }} Bulan {{ selectChineseDate.month }}
    </h2>
  </div>
</template>

<script>
import { CalendarChinese } from 'date-chinese';

export default {
  todayDate: null,
  chineseDate: null,
  selectedDate: null,
  selectChineseDate: null,
  created() {
    const calendarChinese = new CalendarChinese();
    this.todayDate = new Date('2022 June 19');
    this.chineseDate = calendarChinese.fromDate(this.todayDate);
    console.log(this.chineseDate);
  },
  methods: {
    selectDate() {
      this.selectChineseDate = calendarChinese.fromDate(this.selectDate)
    }
  }
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
