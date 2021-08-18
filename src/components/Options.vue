<template>
  <div class="dropdown">
    <button class="dropBtn"><img class="icon" src="../assets/icons/options.svg"/></button>
    <div class="options">
      <hr class="shr">
      <span class="option intervals">Interval: <a id="one" class="selected" style="margin-left: .5rem;" href="javascript:void(0)">1m</a><a id="five" style="margin-left: 1rem;" href="javascript:void(0)">5m</a></span>
      <hr class="ihr">
      <span class="option alertP">Alert point: <a id="fifty" style="margin-left: .5rem;" href="javascript:void(0)">50%</a><a id="dbl" class="selected" style="margin-left: 1rem;" href="javascript:void(0)">100%</a><a id="onefif" style="margin-left: 1rem;" href="javascript:void(0)">150%</a></span>
      <hr class="ihr">
      <span class="option alertS">Alert sound: <a id="soundon" class="selected" style="margin-left: .5rem;" href="javascript:void(0)">On</a><a id="soundoff" style="margin-left: 1rem;" href="javascript:void(0)">Off</a></span>
    </div>
  </div>
</template>

<!--
let intervalOption = 'one';
document.querySelector('.intervals').addEventListener('click', function(event) {
  interval = parseInt(document.querySelector(`#${event.target.id}`).innerHTML);
  document.querySelector(`#${intervalOption}`).classList.remove('selected');
  document.querySelector(`#${event.target.id}`).classList.add('selected');
  intervalOption = event.target.id;
});

let alertOption = 'dbl';
document.querySelector('.alertP').addEventListener('click', function(event) {
  alertPoint = parseFloat(document.querySelector(`#${event.target.id}`).innerHTML) / 100;
  document.querySelector(`#${alertOption}`).classList.remove('selected');
  document.querySelector(`#${event.target.id}`).classList.add('selected');
  alertOption = event.target.id;
});

let soundOption = 'soundon';
document.querySelector('.alertS').addEventListener('click', function(event) {
  if (event.target.id === 'soundon') {
    sounds = true;
  } else if (event.target.id ==='soundoff') {
    sounds = false;
  };
  document.querySelector(`#${soundOption}`).classList.remove('selected');
  document.querySelector(`#${event.target.id}`).classList.add('selected');
  soundOption = event.target.id;
});
-->

<script>
import CoinBox from './CoinBox.vue'
import CoinInput from './CoinInput.vue'
import Logs from './Logs.vue'

export default {
  name: 'Options'
}
</script>

<style>
.icon {
  width: 2rem;
}

.dropdown {
  position: relative;
  display: inline-block;
}

.dropBtn {
  color: #f3ecce;
  font-size: 1.45rem;
  border-radius: 5px;
  margin-left: 0;
  padding: 0px 0px 0px 2px;
}

.dropdown:hover {
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}

.dropdown:hover .dropBtn {
  background-color: #303a52;
  border-bottom-left-radius: 0;
  border-bottom-right-radius: 0;
}

.ihr {
  border: 1px solid #303a52;
  border-radius: 5px;
  width: 60%;
  margin-top: .5rem;
  margin-bottom: .5rem;
}

.shr {
  border: 1px solid #f3ecce;
  border-radius: 5px;
  width: 60%;
  margin-top: .5rem;
  margin-bottom: 1rem;
}

.option {
  padding-left: 1rem;
  color: #F7F2DE;
  letter-spacing: -1px;
}

.options a:hover {
  color: grey;
}

.dropdown:hover .options {
  display: block;
}

.option .selected {
  color: #dab367;
  font-weight: bold;
}

.options {
  display: none;
  position: absolute;
  background-color: #303a52;
  width: 16.5rem;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
  border-bottom-left-radius: 5px;
  border-bottom-right-radius: 5px;
  border-top-right-radius: 5px;
  padding-top: 0;
  padding-bottom: 1rem;
  font-family: 'Typori';
  font-size: 1.15rem;
}

.options a {
  color: dimgrey;
  margin-left: .5rem;
  text-decoration: none;
  margin: 0;
}
</style>