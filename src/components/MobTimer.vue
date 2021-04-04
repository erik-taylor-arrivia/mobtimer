<template>
  <div id="mobWrapper">
    <div class="container">
      <h2>{{title}}</h2>
      <div id="timer">
        <span id="minutes">{{ minutes }}</span>
        <span id="middle">:</span>
        <span id="seconds">{{ seconds }}</span>
      </div>
      <span id="buttons">
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
      <div id="alert" class="alert alert-success alert-dismissible fade show d-none" role="alert">
        <strong>Holy guacamole!</strong> You should check in on some of those fields below.
        <button type="button" class="close" data-dismiss="alert" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MobTimer',
  data() {
    return {
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
    }
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => this.countdown(), 1000);
      this.resetButton = true;
      this.title = "Time to earn ya keep"
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
      this.title = "Restart da work"
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
    margin: 0.5em;

    .far {
      margin: 0 0.25em;
    }
  }
</style>