<template>
  <div class="coinBox">
    <p class="labels">
      <span class="pairlabel">Pair</span>
      <span class="priceLabel">Price</span>
      <span class="statLabel">24hr%</span>
      <span class="intLbl">Intrv%<span class="intTool">The price change for the interval of time that you set.</span></span>
      <span class="volLabel">CurVol/Min | AveVol/Min<span class="vmTool">This compares the volume per minute for the interval of time that you set, to the average volume per minute for the last 3 hours. The average value is updated every hour. Everytime the current vol/m ticks higher than the ave vol/m, above your set alert point, it will be highlighted and added to the log.</span></span>
      <span class="removeLabel">Remove</span>
    </p>
    <hr class="hr">
    <h2 class="placehold">Click the + button or press Enter to add a coin pair.</h2>
  </div>
</template>

<!--
function deleteCoin(pair) {
  let shitCoin;
  coins.forEach(coin => {
    if (coin.name === pair) {
      shitCoin = coin.index;
    }
  });
  coins.splice(shitCoin, 1);

  displayBlankCoins();
}

function displayBlankCoins() {
  let counter = 0;
  if (coins.length === 0) {
    document.querySelector('.notifications').innerHTML = `
    <hr class="shr">
    <h4 class="phold">Add some coin pairs!</h4>
    `;
    document.querySelector('.coinBox').innerHTML = `
    <p class="labels">
      <span class="pairlabel">Pair</span>
      <span class="priceLabel">Price</span>
      <span class="statLabel">24hr%</span>
      <span class="intLbl">${interval}min%<span class="intTool">The price change for the interval of time that you set.</span></span>
      <span class="volLabel">CurVol/Min | AveVol/Min<span class="vmTool">This compares the volume per minute for the interval of time that you set, to the average volume per minute for the last 3 hours. The average value is updated every hour. Everytime the current vol/m ticks higher than the ave vol/m, above your set alert point, it will be highlighted and added to the log.</span></span>
      <span class="removeLabel">Remove</span>
    </p>
    <hr class="hr">
    <h2 class="placehold">Click the + button or press Enter to add a coin pair.</h2>
    `;
    document.querySelector('.switch').classList.add('disabled');
    document.querySelector('.switch').disabled = true;
    document.querySelector('.btnTool').textContent = 'Add a coin pair first.';
  } else {
    document.querySelector('.notifications').innerHTML = `
    <hr class="shr">
    `;
    document.querySelector('.coinBox').innerHTML = `
    <p class="labels">
      <span class="pairlabel">Pair</span>
      <span class="priceLabel">Price</span>
      <span class="statLabel">24hr%</span>
      <span class="intLbl">${interval}min%<span class="intTool">The price change for the interval of time that you set.</span></span>
      <span class="volLabel">CurVol/Min | AveVol/Min<span class="vmTool">This compares the volume per minute for the interval of time that you set, to the average volume per minute for the last 3 hours. The average value is updated every hour. Everytime the current vol/m ticks higher than the ave vol/m, above your set alert point, it will be highlighted and added to the log.</span></span>
      <span class="removeLabel">Remove</span>
    </p>
    <hr class="hr">
    `;
    document.querySelector('.switch').classList.remove('disabled');
    document.querySelector('.switch').disabled = false;
    document.querySelector('.btnTool').textContent = 'Start Tracking.';
  };

  coins.forEach(coin => {
    coin.index = counter;
    counter++;
    coin.alertPrice = 0;

    let logHtml;
    if (coin.logs.length === 0) {
      logHtml = `
      <div class="expandbl">
        <button id="${coin.name}DropDown" class="expBtn">${coin.name}</button>
        <div class="logs">
          <span class="logLbl">${coin.name}</span>
          <span id="${coin.name}Bell" class="fakeBtn hidden">
            <img class="bell" src="src/icons/bell.svg"/>
            <span id="${coin.name}AlertTool" class="alertTool"></span>
          </span>
          <div class="alertSetup">
            <span class="alertLbl">Alert when<a id="${coin.name}AlertType" style="margin-left: 4px;margin-right: 4px" href="javascript:void(0)">${coin.alert}</a>than $</span>
            <input id="${coin.name}AlertInput" class="priceAlert" type="text" name="interval" placeholder="TYPE IN PRICE" autocomplete="off">
            <button id="${coin.name}SetAlert" class="alBtn"><img class="check" src="src/icons/ok.svg"/></button>
            <button id="${coin.name}RemoveAlert" class="rmAlrt hidden"><img class="rmAl" src="src/icons/cancel.svg"/></button>
          </div>
          <hr class="shr">
          <div id="${coin.name}Logs">
          <h4 style="text-align: center;">No events logged yet.</h4>
          </div>
        </div>
      </div>
      `;
    } else {
      logHtml = `
      <div class="expandbl">
        <button id="${coin.name}DropDown" class="expBtn">${coin.name}</button>
        <div class="logs">
          <span class="logLbl">${coin.name}</span>
          <span id="${coin.name}Bell" class="fakeBtn hidden">
            <img class="bell" src="src/icons/bell.svg"/>
            <span id="${coin.name}AlertTool" class="alertTool"></span>
          </span>
          <div class="alertSetup">
            <span class="alertLbl">Alert when<a id="${coin.name}AlertType" style="margin-left: 4px;margin-right: 4px" href="javascript:void(0)">${coin.alert}</a>than $</span>
            <input id="${coin.name}AlertInput" class="priceAlert" type="text" name="interval" placeholder="TYPE IN PRICE" autocomplete="off">
            <button id="${coin.name}SetAlert" class="alBtn"><img class="check" src="src/icons/ok.svg"/></button>
            <button id="${coin.name}RemoveAlert" class="rmAlrt hidden"><img class="rmAl" src="src/icons/cancel.svg"/></button>
          </div>
          <hr class="shr">
          <div id="${coin.name}Logs">
          </div>
        </div>
      </div>
      `;
    }

    const coinHtml = `
      <div class="item">
        <span id="${coin.name}Name" class="pair">${coin.name}</span>
        <span id="${coin.name}Price" class="price">--</span>
        <span id="${coin.name}DailyPercent" class="dP">--</span>
        <span id="${coin.name}PricePercent" class="priceP">--</span>
        <span id="${coin.name}Vol" class="vol">-- | --</span>
        <button id="${coin.name}" class="xBtn" type="submit" name="remove">X</button>
      </div>
    `;

    document.querySelector(".coinBox").insertAdjacentHTML('beforeend', coinHtml);
    document.querySelector(".notifications").insertAdjacentHTML('beforeend', logHtml);

    if (coin.logs.length > 0) {
      coin.logs.forEach(log => {
        const html = `
        <h4>${log}</h4>
        `;
        document.querySelector(`#${coin.name}Logs`).insertAdjacentHTML('beforeend', html);
      });
    }
  });

  for (let i = 0; i < document.querySelectorAll('.xBtn').length; i++) {
    document.querySelectorAll('.xBtn')[i].addEventListener("click", function(event) {
      const pair = event.target.id;
      deleteCoin(pair);
    });
  }

  for (let i = 0; i < document.querySelectorAll('.expBtn').length; i++) {
    document.querySelectorAll('.expBtn')[i].addEventListener('mouseenter', function(event) {
      const btn = event.target.id;
      if (document.querySelector(`#${btn}`).classList.contains('pulsing')) {
        document.querySelector(`#${btn}`).classList.remove('pulsing');
      }
    });
  }

  coins.forEach(coin => {
    document.querySelector(`#${coin.name}AlertType`).addEventListener('click', function() {
      if (document.querySelector(`#${coin.name}AlertType`).textContent === 'lower') {
        document.querySelector(`#${coin.name}AlertType`).textContent = 'higher';
        coin.alert = 'higher';
      } else {
        document.querySelector(`#${coin.name}AlertType`).textContent = 'lower';
        coin.alert = 'lower';
      }
    });

    document.querySelector(`#${coin.name}SetAlert`).addEventListener('click', function() {
      let userInput = document.querySelector(`#${coin.name}AlertInput`).value;
      let alertPrice = parseFloat(userInput);
      
      if (isNaN(alertPrice)) {
        alert('Please enter a valid number.');
      } else {
        coin.alertPrice = alertPrice;
        document.querySelector(`#${coin.name}AlertInput`).value = '';
        document.querySelector(`#${coin.name}RemoveAlert`).classList.remove('hidden');
        document.querySelector(`#${coin.name}AlertTool`).innerHTML = `Alert set at: $${alertPrice}`;
        document.querySelector(`#${coin.name}Bell`).classList.remove('hidden');
      }
    });

    document.querySelector(`#${coin.name}RemoveAlert`).addEventListener('click', function() {
      coin.alertPrice = 0;
      document.querySelector(`#${coin.name}RemoveAlert`).classList.add('hidden');
      document.querySelector(`#${coin.name}Bell`).classList.add('hidden');
    });

    document.querySelector(`#${coin.name}AlertInput`).addEventListener('keydown', function(event) {
      if (event.key === "Enter") {
        document.querySelector(`#${coin.name}SetAlert`).click();
      }
    });
  });
}

async function initData() {
  coins.forEach(async(coin) => {
    const priceData = await getPrice(coin.name);
    const volData = await getCurVol(coin.name);
    coin.curPrice = priceData.substring(0, 8);
    coin.curVol = volData.substring(0, 8);
    const dayPercentData = await get24hrPercent(coin.name);
    const convertedData = parseFloat(dayPercentData);
    const dayPricePercent = convertedData.toFixed(2);

    if (dayPricePercent > 0) {
      document.querySelector(`#${coin.name}DailyPercent`).style.color = '#05b114';
      document.querySelector(`#${coin.name}DailyPercent`).innerHTML = `+${dayPricePercent}%`;
    } else {
      document.querySelector(`#${coin.name}DailyPercent`).style.color = '#d2121a';
      document.querySelector(`#${coin.name}DailyPercent`).innerHTML = `${dayPricePercent}%`;
    };

    const aveVol = await getAveVol(coin.name);
    const aveVolMin = aveVol / 60;
    coin.aVm = aveVolMin.toFixed();

    document.querySelector(`#${coin.name}Price`).innerHTML = coin.curPrice;
    document.querySelector(`#${coin.name}Vol`).innerHTML = `xxxxxx/min | ${coin.aVm}/min`;
  });
}

async function displayTickData() {
  setDates();
  
  if (min === 0 && sec < 5) {
    coins.forEach(async(coin) => {
      const aveVol = await getAveVol(coin.name);
      const aveVolMin = aveVol / 60;
      coin.aVm = aveVolMin.toFixed();
      coin.curVol = 0;
    });
  };

  coins.forEach(async(coin) => {
    const priceData = await getPrice(coin.name);
    const dayPercentData = await get24hrPercent(coin.name);
    const price = priceData.substring(0, 8);
    const convertedData = parseFloat(dayPercentData);
    const dayPricePercent = convertedData.toFixed(2);
    
    document.querySelector(`#${coin.name}Price`).innerHTML = price;

    if (dayPricePercent > 0) {
      document.querySelector(`#${coin.name}DailyPercent`).style.color = '#05b114';
      document.querySelector(`#${coin.name}DailyPercent`).innerHTML = `+${dayPricePercent}%`;
    } else {
      document.querySelector(`#${coin.name}DailyPercent`).style.color = '#d2121a';
      document.querySelector(`#${coin.name}DailyPercent`).innerHTML = `${dayPricePercent}%`;
    };

    const floatPrice = parseFloat(price);
    if (coin.alertPrice !== 0) {
      if (coin.alert === 'higher') {
        if (floatPrice >= coin.alertPrice) {
          priceSound.play();
          document.querySelector('#noteDrop').classList.add('pulsing');
          document.querySelector(`#${coin.name}DropDown`).classList.add('pulsing');
          if (min < 10) {
              coin.logs.unshift(`Alert price hit! $${price} at ${hour}:0${min}`);
          } else {
              coin.logs.unshift(`Alert Price hit! $${price} at ${hour}:${min}`);
          }
          document.querySelector(`#${coin.name}Logs`).innerHTML = '';
  
          coin.logs.forEach(log => {
            const html = `
            <h4>${log}</h4>
            `;
            document.querySelector(`#${coin.name}Logs`).insertAdjacentHTML('beforeend', html);
          });
          coin.alertPrice = 0;
          document.querySelector(`#${coin.name}RemoveAlert`).classList.add('hidden');
          document.querySelector(`#${coin.name}Bell`).classList.add('hidden');
        }
      } else {
        if (floatPrice <= coin.alertPrice) {
          priceSound.play();
          document.querySelector('#noteDrop').classList.add('pulsing');
          document.querySelector(`#${coin.name}DropDown`).classList.add('pulsing');
          if (min < 10) {
              coin.logs.unshift(`Alert price hit! $${price} at ${hour}:0${min}`);
          } else {
              coin.logs.unshift(`Alert Price hit! $${price} at ${hour}:${min}`);
          }
          document.querySelector(`#${coin.name}Logs`).innerHTML = '';
  
          coin.logs.forEach(log => {
            const html = `
            <h4>${log}</h4>
            `;
            document.querySelector(`#${coin.name}Logs`).insertAdjacentHTML('beforeend', html);
          });
          coin.alertPrice = 0;
          document.querySelector(`#${coin.name}RemoveAlert`).classList.add('hidden');
          document.querySelector(`#${coin.name}Bell`).classList.add('hidden');
        }
      }
    }
  });
}

async function displayIntData() {
  coins.forEach(async(coin) => {
    coin.lastPrice = coin.curPrice;
    coin.lastVol = coin.curVol;

    if (document.querySelector(`#${coin.name}Vol`).classList.contains('hotVol')) {
      document.querySelector(`#${coin.name}Vol`).classList.remove('hotVol');
    }
    if (document.querySelector(`#${coin.name}Name`).classList.contains('hotCoin')) {
      document.querySelector(`#${coin.name}Name`).classList.remove('hotCoin');
    }

    const priceData = await getPrice(coin.name);
    const volData = await getCurVol(coin.name);
    coin.curPrice = priceData.substring(0, 8);
    coin.curVol = volData.substring(0, 8);
    const priceDiffRaw = (coin.curPrice - coin.lastPrice) / coin.lastPrice;
    const volPerMin = (coin.curVol - coin.lastVol);
    const volPerMinRate = (volPerMin - coin.aVm) / coin.aVm;
    const volPerMinPercent = (volPerMinRate * 100).toFixed();
    const priceDifference = (priceDiffRaw * 100).toFixed(3);
    const volPerMinute = volPerMin.toFixed();

    if (volPerMinRate < alertPoint) {
      if (interval === 1) {
        coin.oneTicks.push(0);

        if (coin.oneTicks.length > 10) {
          coin.oneTicks.shift();
        }
      } else if (interval === 5) {
        coin.fiveTicks.push(0);

        if (coin.fiveTicks.length > 3) {
          coin.fiveTicks.shift();
        }
      }
    }

    if (volPerMinRate >= alertPoint && sounds === true) {
      alertSound.play();
      document.querySelector(`#${coin.name}Vol`).classList.add('hotVol');

      if (interval === 1) {
        coin.oneTicks.push(1);

        if (coin.oneTicks.length > 10) {
          coin.oneTicks.shift();
          const total = coin.oneTicks.reduce((a, b) => a + b, 0);

          if (total >= 7) {
            document.querySelector(`#${coin.name}Name`).classList.add('hotCoin');
            hotSound.play();
          }
        }
      } else if (interval === 5) {
        coin.fiveTicks.push(1);

        if (coin.fiveTicks.length > 3) {
          coin.fiveTicks.shift();
          const total = coin.fiveTicks.reduce((a, b) => a + b, 0);

          if (total >= 2) {
            document.querySelector(`#${coin.name}Name`).classList.add('hotCoin');
            hotSound.play();
          }
        }
      }

      if (coin.logs.length >= 10) {
        coin.logs.pop();
      }

      if (min < 10) {
        if (priceDifference > 0) {
          coin.logs.unshift(`$${coin.curPrice} (+${priceDifference}%) and +${volPerMinPercent}%v/m at ${hour}:0${min}`);
        } else {
          coin.logs.unshift(`$${coin.curPrice} (${priceDifference}%) and +${volPerMinPercent}%v/m at ${hour}:0${min}`);
        }
      } else {
        if (priceDifference > 0) {
          coin.logs.unshift(`$${coin.curPrice} (+${priceDifference}%) and +${volPerMinPercent}%v/m at ${hour}:${min}`);
        } else {
          coin.logs.unshift(`$${coin.curPrice} (${priceDifference}%) and +${volPerMinPercent}%v/m at ${hour}:${min}`);
        }
      }

      document.querySelector('#noteDrop').classList.add('pulsing');
      document.querySelector(`#${coin.name}DropDown`).classList.add('pulsing');

    } else if (volPerMinRate >= alertPoint && sounds === false) {
      document.querySelector(`#${coin.name}Vol`).classList.add('hotVol');

      if (interval === 1) {
        coin.oneTicks.push(1);

        if (coin.oneTicks.length > 10) {
          coin.oneTicks.shift();
          const total = coin.oneTicks.reduce((a, b) => a + b, 0);

          if (total >= 7) {
            document.querySelector(`#${coin.name}Name`).classList.add('hotCoin');
          }
        }
      } else if (interval === 5) {
        coin.fiveTicks.push(1);

        if (coin.fiveTicks.length > 3) {
          coin.fiveTicks.shift();
          const total = coin.fiveTicks.reduce((a, b) => a + b, 0);

          if (total >= 2) {
            document.querySelector(`#${coin.name}Name`).classList.add('hotCoin');
          }
        }
      }

      if (coin.logs.length >= 10) {
        coin.logs.pop();
      }

      if (min < 10) {
        if (priceDifference > 0) {
          coin.logs.unshift(`$${coin.curPrice} (+${priceDifference}%) and +${volPerMinPercent}%v/m at ${hour}:0${min}`);
        } else {
          coin.logs.unshift(`$${coin.curPrice} (${priceDifference}%) and +${volPerMinPercent}%v/m at ${hour}:0${min}`);
        }
      } else {
        if (priceDifference > 0) {
          coin.logs.unshift(`$${coin.curPrice} (+${priceDifference}%) and +${volPerMinPercent}%v/m at ${hour}:${min}`);
        } else {
          coin.logs.unshift(`$${coin.curPrice} (${priceDifference}%) and +${volPerMinPercent}%v/m at ${hour}:${min}`);
        }
      }

      document.querySelector('#noteDrop').classList.add('pulsing');
      document.querySelector(`#${coin.name}DropDown`).classList.add('pulsing');
    };

    document.querySelector(`#${coin.name}Vol`).innerHTML = `${volPerMinute}/min | ${coin.aVm}/min`;

    if (priceDifference > 0) {
      document.querySelector(`#${coin.name}PricePercent`).style.color = '#05b114';
      document.querySelector(`#${coin.name}PricePercent`).innerHTML = `+${priceDifference}%`;
    } else {
      document.querySelector(`#${coin.name}PricePercent`).style.color = '#d2121a';
      document.querySelector(`#${coin.name}PricePercent`).innerHTML = `${priceDifference}%`;
    };

    if (coin.logs.length === 0) {
      document.querySelector(`#${coin.name}Logs`).innerHTML = '<h4 style="text-align: center;">No events logged yet.</h4>';
    } else {
      document.querySelector(`#${coin.name}Logs`).innerHTML = '';

      coin.logs.forEach(log => {
        const html = `
        <h4>${log}</h4>
        `;
        document.querySelector(`#${coin.name}Logs`).insertAdjacentHTML('beforeend', html);
      });
    }
  });
}
-->

<script>
import CoinInput from './CoinInput.vue'
import Logs from './Logs.vue'
import Options from './Options.vue'

export default {
  name: 'CoinBox'
}
</script>

<style>
.hotVol {
  background: linear-gradient(to right, #e49039 48%, #2a3347 50%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.hotName {
  background: #e49039;
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.coinBox {
  width: 55rem;
  margin: .5rem auto 3rem;
  background: #F7F2DE;
  border-radius: 5px;
}

.labels {
  display: flex;
  justify-content: space-between;
  font-family: 'Typori';
  font-size: 80%;
  color: grey;
  padding-bottom: .5rem;
}

p {
  margin: 0;
  padding: 20px;
  font-size: 20px;
  color: #00204a;
}

.pairlabel {
  margin-right: 5rem;
  margin-left: 1.6rem;
}

.statLabel {
  margin-left: 1rem;
  margin-right: .5rem;
}

.intLbl {
  margin-left: 1rem;
  margin-right: .5rem;
  border-bottom: 1px dotted grey;
  position: relative;
}

.intLbl .intTool {
  visibility: hidden;
  width: 8rem;
  background-color: #3B3A45;
  color: #F7F2DE;
  text-align: center;
  padding: 5px 0;
  border-radius: 6px;
  position: absolute;
  z-index: 1;
  bottom: 250%;
  left: 50%;
  margin-left: -4rem;
  opacity: 0;
  transition: opacity 0.3s;
}

.intLbl:hover .intTool {
  visibility: visible;
  opacity: .9;
}

.priceLabel {
  margin-left: 0;
  padding-right: 1rem;
}

.volLabel {
  margin-left: 1.7rem;
  margin-right: .2rem;
  padding-right: 0;
  position: relative;
  border-bottom: 1px dotted grey;
}

.volLabel .vmTool {
  visibility: hidden;
  width: 15rem;
  background-color: #3B3A45;
  color: #F7F2DE;
  text-align: center;
  padding: 5px 0;
  border-radius: 6px;
  position: absolute;
  z-index: 1;
  bottom: 250%;
  left: 50%;
  margin-left: -7.5rem;
  opacity: 0;
  transition: opacity 0.3s;
}

.volLabel:hover .vmTool {
  visibility: visible;
  opacity: .9;
}

.removeLabel {
  margin-left: .8rem;
  margin-right: 1rem;
}

.hr {
  width: 70%;
  margin-top: 1rem;
  margin-bottom: 1.5rem;
  border: 1px solid #131420;
  border-radius: 5px;
}

.placehold {
  font-family: 'Maki';
  color: grey;
  text-align: center;
  font-weight: lighter;
  font-size: 115%;
  margin-top: 1.5rem;
  /* margin-bottom: 1.5rem; */
  padding-bottom: 1.5rem;
}

.pair {
  font-family: 'DPS';
  font-size: 120%;
  color: #2a3347;
  min-width: 6rem;
  letter-spacing: -1px;
  margin-left: .5rem;
}

.price{
  font-family: 'Sax';
  font-size: 95%;
  color: #2a3347;
  min-width: 4rem;
}

.priceP{
  font-family: 'Sax';
  font-size: 95%;
  color: #2a3347;
  min-width: 2.5rem;
}

.vol, .pvol{
  font-family: 'Sax';
  font-size: 95%;
  color: #2a3347;
  min-width: 12rem;
  text-align: center;
}

.dP{
  font-family: 'Sax';
  font-size: 95%;
  color: #2a3347;
  min-width: 3.5rem;
}

.xBtn {
  margin-left: 0rem;
  font-size: 1.5rem;
  min-height: 40px;
  width: 40px;
}

.item {
  display: flex;
  align-items: center;
  justify-content: space-around;
  font-weight: bold;
}

.item:last-child {
  padding-bottom: 1rem;
}
</style>