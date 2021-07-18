<template>
  <div class="box">
    <div v-if="selected === 'name'" class="box__item box__name">
      <form action="" @submit.prevent="toTime">
        <input type="text" v-model="name" />
        <center>
          <button class="btn">OK</button>
        </center>
      </form>
    </div>

    <div v-if="selected === 'time'" class="box__item box__time">
      <h3>{{ name }}</h3>
      <button class="btn" @click="setTime(5)">5min</button>
      <button class="btn" @click="setTime(10)">10min</button>
    </div>

    <div v-if="selected === 'loading'" class="box__item box__loading">
      <h3>{{ name }}</h3>
      <h2>{{ prettyTime }}</h2>
      <div class="loading">
        <span ref="loadingLine"></span>
      </div>
      <button class="btn btn--blue" @click="resetTimer(true)">Reset</button>
    </div>

    <div v-if="selected === 'ready'" class="box__item box__ready">
      <button class="btn btn--blue" @click="resetTimer(false)">Reset</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Box",
  data() {
    return {
      name: "",
      //name / time / loading / ready
      selected: "name",
      start: 0,
      isRunning: false,
      minutes: 0,
      secondes: 0,
      time: 0,
      timer: null,
      selectedMin: 0,
    };
  },
  computed: {
    prettyTime() {
      let time = this.time / 60;
      let minutes = parseInt(time);
      let secondes = Math.round((time - minutes) * 60);
      return minutes + ":" + secondes;
    },
  },
  methods: {
    setTime(payload) {
      this.selectedMin = payload;
      this.time = payload * 60;
      this.startTimer();
      this.selected = "loading";
    },
    toTime() {
      if (this.name) {
        this.selected = "time";
      }
    },
    stopTimer() {
      this.isRunning = false;
      clearInterval(this.timer);
      this.timer = null;
    },
    reset() {
      this.stopTimer();
      this.time = 0;
      this.secondes = 0;
      this.minutes = 0;
      this.selectedMin = 0;
    },
    startTimer() {
      this.isRunning = true;
      if (!this.timer) {
        this.timer = setInterval(() => {
          if (this.time > 0) {
            this.time--;
            // console.log(this.$refs.loadingLine.style.width);
            // // this.$refs.loadingLine
            // // this.$refs.loadingLine.style.width = this.time;
            // console.log((this.time * 100) / (this.selectedMin * 60));
          } else {
            clearInterval(this.timer);
            this.reset();
            this.selected = "ready";
          }
        }, 1000);
      }
    },
    resetTimer(type) {
      if (type) {
        let result = confirm("Reset Timer?");
        if (result) {
          this.selected = "name";
          this.name = "";
        }
      } else {
        this.selected = "name";
        this.name = "";
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
