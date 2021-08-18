<template>
  <div class="inputBox">
    <div class="input">
      <input class="coinInput" type="text" name="newItem" placeholder="Coin pair. No slashes/dashes, ex. BTCUSDT" autocomplete="off">
      <button class="add" type="submit" name="add">+</button>
      <button class="switch disabled" type="submit" name="switch" disabled>><span class="btnTool">Add a coin pair first.</span></button>
    </div>
  </div>
</template>

<!--
function startTracking(int) {
  let ms = int * 60000;
  document.querySelector('.xBtn').disabled = true;
  document.querySelector('.xBtn').classList.add('disabled');
  coins.forEach(coin => {
    document.querySelector(`#${coin.name}`).disabled = true;
    document.querySelector(`#${coin.name}`).classList.add('disabled');
  });
  ticker = setInterval(displayTickData, 4000);
  tracking = setInterval(displayIntData, ms);
}

function stopTracking() {
  clearInterval(ticker);
  clearInterval(tracking);
}

function addCoin(pair) {
  pair = new Coin(pair);
  coins.push(pair);

  displayBlankCoins();
}

document.querySelector('.add').addEventListener('click', function() {
  let userInput = document.querySelector('.coinInput').value;
  let pairing = userInput.toUpperCase();
  
  document.querySelector('.coinInput').value = '';

  if (document.querySelector(`#${pairing}`)) {
    alert('This pair was already added.');
  } else {
    fetch(`https://api.binance.com/api/v3/ticker/price?symbol=${pairing}`).then(function(res) {
    addCoin(pairing);
  }).catch(function(err) {
    alert('Please enter a valid coin pairing. Make sure not to use dashes or slashes.');
  });
  }
});

document.querySelector('.coinInput').addEventListener('keydown', function(event) {
  if (event.key === "Enter") {
    document.querySelector('.add').click();
  }
});

document.querySelector('.switch').addEventListener('click', function() {
  if (document.querySelector('.switch').innerHTML === 'II<span class="btnTool">Stop Tracking.</span>') {
    document.querySelector('.switch').innerHTML = '><span class="btnTool">Start Tracking.</span>';
    document.querySelector('.switch').classList.add('disabled');
    document.querySelector('.switch').disabled = true;
    document.querySelector('.add').classList.remove('disabled');
    document.querySelector('.add').disabled = false;
    document.querySelector('.coinInput').disabled = false;
    document.querySelector('.intervals').classList.remove('noClick');
    document.querySelector('.intervals').style.color = '#F7F2DE';

    stopTracking();
    displayBlankCoins();
  } else {
    document.querySelector('.switch').innerHTML = 'II<span class="btnTool">Stop Tracking.</span>';
    document.querySelector('.add').disabled = true;
    document.querySelector('.add').classList.add('disabled');
    document.querySelector('.coinInput').disabled = true;
    document.querySelector('.intervals').classList.add('noClick');
    document.querySelector('.intervals').style.color = 'dimgrey';

    initData();
    startTracking(interval);
  };
});
-->

<script>
import CoinBox from './CoinBox.vue'
import Logs from './Logs.vue'

export default {
  name: 'CoinInput'
}
</script>

<style>
.inputBox {
  width: 36rem;
  margin: 3rem auto;
  background: #F7F2DE;
  border-radius: 5px;
  /* display: inline-block; */ /*look up why this*/
}

.coinInput {
  padding-left: 2rem;
  padding-bottom: .2rem;
  height: 60px;
  top: 10px;
  border: none;
  background: transparent;
  font-family: 'Maki';
  font-size: 110%;
  width: 313px;
}

::placeholder {
  color: grey;
  font-family: 'Typori';
  opacity: 1;
  font-size: 78%;
}

input[type="text"]:focus {
  outline: none;
}

button {
  min-height: 50px;
  width: 50px;
  color: #131420;
  background: none;
  border: none;
  outline: none;
  font-size: 260%;
  margin-left: 4.5rem;
  cursor: pointer;
}

button:hover {
  color: #475572;
}

.input{
  display: flex;
  align-items: center;
  justify-content: space-around;
}

.switch {
  padding-right: 1.5rem;
  margin-left: 0rem;
  margin-bottom: 2px;
  min-height: 40px;
  width: 40px;
  font-size: 220%;
  position: relative;
}

.switch .btnTool {
  visibility: hidden;
  width: 12rem;
  background-color: #3B3A45;
  color: #F7F2DE;
  text-align: center;
  padding: 5px 0;
  border-radius: 6px;
  position: absolute;
  z-index: 1;
  bottom: 130%;
  left: 50%;
  margin-left: -10rem;
  opacity: 0;
  transition: opacity 0.3s;
  font-family: 'Typori';
  font-size: 1rem;
}

.switch:hover .btnTool {
  visibility: visible;
  opacity: .9;
}
</style>