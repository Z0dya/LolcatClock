<template>
  <div class="main">
    <div class="container">
      <div class="timer">
        <h1 class="timer-title">LOLCAT CLOCK</h1>
        <p>Your time is </p>
        <span>{{ time }}</span>
      </div>
      <div class="funnyImg">
        <img src="../assets/cat-chill.gif" alt="GoodMorning" v-if="isCatChill" />
        <img src="../assets/cat-vibe.gif" v-else />
      </div>
      <div class="partyBtn">
        <button class="Btn" @click="partyBtn()">{{ partyText }}</button>
      </div>
    </div>
    <div class="footer">
      <p class="footer-text">This is a copy of an already existing site, I just made an analogue in order to practice my skills</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      time: '',
      isCatChill: true,
      partyText: 'PARTY OVER!',

    }
  },
  created() {
    setInterval(this.getCurrentTime, 100);
  },
  methods: {
    getCurrentTime() {
      // Запись в переменную 
      const date = new Date();
      const hours = date.getHours();
      const minutes = date.getMinutes();
      const dateTime = ("0" + hours).slice(-2) + ": " + ("0" + minutes).slice(-2) + ": " + date.getSeconds();
      this.time = dateTime;
    },
    partyBtn() {
      if (this.isCatChill) {
        this.isCatChill = !this.isCatChill;
        this.partyText = 'PARTY TIME!';
      }
      else {
        this.isCatChill = !this.isCatChill
        this.partyText = 'PARTY OVER!';
      }
    }
  }
}
</script>

<style scoped lang="scss">
%center {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

p {
  margin: 0;
  padding: 0;
}

h1 {
  margin: 5rem 0 0 0;
}

.main {
  height: 100%;
  position: relative;
}

.container {
  @extend %center;

  .timer {
    @extend %center;
    font-size: 3rem;
    text-align: center;

    .timer-title {
      font-family: 'Bungee Shade', cursive;
      font-size: 5rem;
    }
  }

  .partyBtn {

    .Btn {
      margin-top: 5rem;
      height: 5rem;
      font-size: 2rem;
      font-family: 'Bungee', cursive;
      width: 30rem;
      background-color: #2b2b2b;
      color: white;
      border-radius: 1rem;
      border: none;
      cursor: pointer;
      transition: all 0.2s ease;

    }

    .Btn:hover {
      background-color: #474747;
    }
  }

  .funnyImg {
    margin-top: 2rem;
    width: 30rem;
  }
}

.footer {
  position: absolute;
  bottom: 1px;
  display: flex;
  justify-content: center;
  width: 100%;
  font-size: 1rem;
}


@media (max-width: 590px) {
  .footer-text {
    width: 80%;
    text-align: center;
  }

  .Btn {
    margin-top: 2rem !important;
  }

  h1 {
    margin-top: 0;
  }
}
</style>
