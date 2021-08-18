<template>
  <div id="heading">
    <h1> BVE </h1>
  </div>
  <div class="userDash">
    <Logs />
    <Options />
  </div>
  <CoinInput />
  <CoinBox />
  <div class="about">
    <p class="info">This is Big Volume Energy. Track all your favorite coins from Binance for volume and price spikes. Real-time tracking along with alerts. Simple, lightweight, and it can be run as a local file in your browser. Never miss another pump or breakout again. Just type in some coin pairs above and get started! Check the log on the top-left for events and even set price alerts!</p>
  </div>
  <Footer />
</template>

<!--
let date;
let year;
let month;
let day;
let hour;
let min;
let sec;

let prevHour;
let foHrs;
let prevDay;
let oneDay;
let foDay;

let startDate;
let prevDate;
let foDate;

let startTS;
let curTS;
let prevTS;
let foTS;

function setDates() {
  date = new Date();
  year = date.getFullYear();
  month = date.getMonth();
  day = date.getDate();
  hour = date.getHours();
  min = date.getMinutes();
  sec = date.getSeconds();

  if (day === 0) {
    prevDay = 6;
  } else {
    prevDay = day - 1;
  };

  if ((hour - 4 ) < 0) {
    foHrs = (hour - 4) + 24;
    foDay = prevDay;
  } else {
    foHrs = hour - 6;
    foDay = day;
  };

  if (hour === 0) {
    prevHour = 23;
    oneDay = prevDay;
  } else {
    prevHour = hour - 1;
    oneDay = day;
  };

  startDate = new Date(year, month, day, hour, 0, sec);
  prevDate = new Date(year, month, oneDay, prevHour, min, sec);
  foDate = new Date(year, month, foDay, foHrs, 0, sec );
  startTS = startDate.getTime();
  curTS = date.getTime();
  prevTS = prevDate.getTime();
  foTS = foDate.getTime();
}

setDates();

async function getCurVol(pair) {
  try {
    const res = await fetch('https://api.binance.com/api/v3/klines?symbol=' + pair + '&interval=1h&startTime=' + prevTS + '&endTime=' + curTS);
    const data = await res.json();
    return data[0][5];
  } catch (error) {
    console.error(error);
  }
};

async function getAveVol(pair) {
  try {
    const res = await fetch('https://api.binance.com/api/v3/klines?symbol=' + pair + '&interval=1h&startTime=' + foTS + '&endTime=' + prevTS);
    const data = await res.json();
    const vol1 = parseFloat(data[0][5]);
    const vol2 = parseFloat(data[1][5]);
    const vol3 = parseFloat(data[2][5]);
    const aveVol = ((vol1 + vol2 + vol3) / 3);
    return aveVol;
  } catch (error) {
    console.error(error);
  }
};

async function get24hrPercent(pair) {
  try {
    const res = await fetch('https://api.binance.com/api/v3/ticker/24hr?symbol=' + pair);
    const data = await res.json();
    return data.priceChangePercent;
  } catch (error) {
    console.error(error);
  }
};

async function getPrice(pair) {
  try {
    const res = await fetch('https://api.binance.com/api/v3/ticker/price?symbol=' + pair);
    const data = await res.json();
    return data.price;
  } catch (error) {
    console.error(error);
  }
};

let tracking;
let ticker;
const coins = [];
let interval = 1;
const alertSound = new Audio('src/sound/boop.wav');
const hotSound = new Audio('src/sound/volAlert.wav');
const priceSound = new Audio('src/sound/priceAlert.wav');
let sounds = true;
let alertPoint = 1.0;
-->

<script>
import CoinBox from './components/CoinBox.vue'
import CoinInput from './components/CoinInput.vue'
import Footer from './components/Footer.vue'
import Logs from './components/Logs.vue'
import Options from './components/Options.vue'

export default {
  name: 'App',
  components: {
    CoinBox,
    CoinInput,
    Footer,
    Logs,
    Options
  }
}
</script>

<style>
@font-face {
  font-family: 'Vitreous';
  src: url(./assets/fonts/Vitreous-Heavy.ttf);
}
@font-face {
  font-family: 'Typori';
  src: url(./assets/fonts/Typori-Regular.ttf);
}
@font-face {
  font-family: 'Maki';
  src: url(./assets/fonts/MAKISUPA.TTF);
}
@font-face {
  font-family: 'DPS';
  src: url(./assets/fonts/DPSDbeyond.otf);
}
@font-face {
  font-family: 'Sax';
  src: url(./assets/fonts/saxmono.ttf);
}

html {
  background: linear-gradient(157deg, rgba(19,20,32,1) 0%, rgba(29,26,45,1) 50%, rgba(19,20,32,1) 100%);
  height: 100%;
  background-repeat: no-repeat;
  background-attachment: fixed;
}

body {
  margin: 0;
  min-height: 100%;
  /* display: grid;
  grid-template-rows: auto auto auto 1fr auto; 
  
  no longer works - all in 1 div now
  */
}

.disabled {
  color: grey;
  cursor: default;
}

.disabled:hover {
  color: grey;
}

@keyframes pulse {
  from { transform: scale(1); }
  50% { transform: scale(1.2); }
  to { transform: scale(1); }
}

.pulsing {
  animation-name: pulse;
  animation-duration: 1s;
  animation-iteration-count: infinite;
}

.noClick {
  pointer-events: none;
}

#heading {
  text-align: center;
  margin-bottom: 2rem;
  margin-right: auto;
  margin-left: auto;
  border-radius: 5px;
}

h1 {
  background: linear-gradient(to bottom right, #C54C24 0%, #dab367 50%, #C54C24 100%);
  background-clip: unset;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  font-family: 'Vitreous';
  font-size: 14rem;
  margin-top: 0;
  margin-bottom: 0;
  padding-left: 4px;
  letter-spacing: 2px;
}

.userDash {
  position: fixed;
  top: 2%;
  left: 1%;
  display: inline-block;
}

.about {
  width:58rem;
  margin-left: auto;
  margin-right: auto;
}

.info {
  text-align: center;
  font-family: 'Typori';
  font-size: 1.1rem;
  color: grey;
  margin-bottom: 2.5rem;
}
</style>
