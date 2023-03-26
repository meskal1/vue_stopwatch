<script>
export default {
  name: "CounterItem",
  data() {
    return {
      hours: 0,
      minutes: 0,
      seconds: 0,
      isActive: false,
    };
  },
  methods: {
    handleToggleStart() {
      if (this.isActive) {
        clearInterval(this.counter);
        this.isActive = false;
      } else {
        this.counter = setInterval(() => {
          if (this.minutes === 59 && this.seconds === 59) {
            this.hours += 1;
            this.minutes = 0;
            this.seconds = 0;
            return;
          }

          if (this.seconds === 59) {
            this.minutes += 1;
            this.seconds = 0;
            return;
          }

          this.seconds += 1;
        }, 1000);
        this.isActive = true;
      }
    },

    handleReset() {
      this.hours = 0;
      this.minutes = 0;
      this.seconds = 0;

      if (this.isActive) {
        this.isActive = false;
        clearInterval(this.counter);
      }
    },
  },
};
</script>

<template>
  <div class="counter-container" :class="{ active: isActive }">
    <div class="displayed-count">
      {{ hours ? hours + ":" + minutes + ":" : null
      }}{{ !hours && minutes ? minutes + ":" : null }}{{ seconds }}
    </div>
    <div class="buttons">
      <button class="start-stop" @click="handleToggleStart" />
      <button class="reset" @click="handleReset" />
    </div>
  </div>
</template>

<style scoped>
.counter-container {
  display: flex;
  flex-direction: column;
  flex: 0 1 225px;
  background: #696969;
}
.displayed-count {
  color: #9e9e9e;
  padding: 19px 0;
  text-align: center;
  border-bottom: 1px solid #9e9e9e;
}
.buttons {
  display: flex;
  justify-content: space-between;
  padding: 19px 70px;
}
.start-stop {
  position: relative;
  cursor: pointer;
  border-top: 10px solid transparent;
  border-bottom: 10px solid transparent;
  background: transparent;
  border-left: 17px solid #9e9e9e;
}
.reset {
  cursor: pointer;
  width: 20px;
  height: 20px;
  background: #9e9e9e;
}
.active .start-stop::before,
.active .start-stop::after {
  position: absolute;
  content: "";
  top: -10px;
  width: 3px;
  height: 20px;
  background: white;
}
.active .start-stop::before {
  left: -13px;
}
.active .start-stop::after {
  left: -6px;
}
.active .start-stop {
  border-left: 17px solid transparent;
}
.active .reset {
  background: white;
}
.active .displayed-count {
  border-bottom: 1px solid white;
  color: white;
}
</style>
