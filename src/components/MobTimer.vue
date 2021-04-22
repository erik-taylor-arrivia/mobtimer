<template>
  <div id="mobWrapper">
    <div class="container">
      <h2>{{title}}</h2>
      <!-- <form class="mt-3 mb-3 form-inline justify-content-center" v-on:submit.prevent="">
        <div class="row">
          <div class="form-group col-auto p-0">
            <input
              type="number"
              id="interval"
              step='1'
              min='1'
              v-model.number="time"
              class="form-control"
              placeholder="Set interval">
          </div>
          <div class="form-group col-auto">
            <button
              :disabled="submitIsDisabled"
              class="btn btn-primary">
              Change
            </button>
          </div>
        </div>
      </form> -->

      <div id="timer">
        <span id="minutes">{{ minutes }}</span>
        <span id="middle">:</span>
        <span id="seconds">{{ seconds }}</span>
      </div>

      <span id="buttons" class="btn-group" role="group">
        <button
          id="start"
          class="btn btn-primary"
          v-if="!timer"
          @click="startTimer">
            Start Timer
            <i class="far fa-play-circle"></i>
        </button>
        <button
          id="stop"
          class="btn btn-primary"
          v-if="timer"
          @click="stopTimer">
            Stop Timer
            <i class="far fa-pause-circle"></i>
        </button>
        <button
          id="reset"
          class="btn btn-danger"
          v-if="resetButton"
          @click="resetTimer">
            Reset Timer
            <i class="fas fa-undo"></i>
        </button>
      </span>

    </div>
  </div>
</template>

<script>
export default {
  name: 'MobTimer',
  data() {
    return {
      time: null,
      timer: null,
      totalTime: (20 * 60),
      resetButton: false,
      title: "Join the Family"
    }
  },
  computed: {
    minutes() {
      const minutes = Math.floor(this.totalTime / 60);
      return this.padTime(minutes);
    },
    seconds() {
      const seconds = this.totalTime - (this.minutes * 60);
      return this.padTime(seconds);
    },
    // submitIsDisabled() {
    //   return this.time == null;
    // }
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => this.countdown(), 1000);
      this.resetButton = true;
      this.title = "Work started"
    },
    stopTimer() {
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = true;
      this.title = "Get back ta work"
    },
    resetTimer() {
      this.totalTime = (20 * 60);
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = false;
      this.title = "Join the Family"
    },
    padTime(time) {
      return (time < 10 ? '0' : '') + time;
    },
    countdown() {
      if(this.totalTime >= 1){
        this.totalTime--;
      } else{
        this.totalTime = 0;
        alert("Time ta switch drivers");
        this.resetTimer()
      }
    }
  }
}
</script>

<style scoped lang="scss">
  #mobWrapper {
    padding: 0em 0 1em;
  }

  #timer {
    font-size: 4em;
  }

  button {
    margin: 0;

    .far {
      margin: 0 0.25em;
    }
  }
</style>