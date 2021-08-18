<template>
  <div id="noteDrop" class="dropdown" :class="{ pulsing: pulsing }" @mouseenter="calm">
    <button class="dropBtn"><img class="icon" src="../assets/icons/notes.svg"/></button>
    <div class="notifications">
      <hr class="shr">
      <h4 class="phold">Add some coin pairs!</h4>
    </div>
  </div>
</template>

<script>
import CoinBox from './CoinBox.vue'
import CoinInput from './CoinInput.vue'
import Options from './Options.vue'

export default {
  name: 'Logs',

  data() {
    return {
      pulsing: false
    }
  },

  methods: {
    calm() {
      if (this.pulsing) {
        this.pulsing = !this.pulsing;
      }
    }
  }
}
</script>

<style>
.expandbl {
  position: relative;
  display: inline-block;
}

.expBtn {
  color: #f3ecce;
  font-size: 1.15rem;
  font-family: 'Typori';
  font-weight: bold;
  margin-left: 0;
  padding: 0px 0px 0px 2px;
  width: 7.2rem;
  min-height: 2rem;
}

hr {
  border: dotted #131420 5px;
  border-bottom: none;
  width: 40%;
  margin-top: 1rem;
  margin-bottom: 1rem;
}

.expandbl:hover .logs {
  display: inline-block;
}

.dropdown:hover .notifications{
  display: block;
}

.notifications {
  display: none;
  position: absolute;
  background-color: #303a52;
  width: 7rem;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
  border-bottom-left-radius: 5px;
  border-bottom-right-radius: 5px;
  border-top-right-radius: 5px;
  padding-top: 0;
  padding-bottom: .5rem;
}

.phold {
  color: grey;
  text-align: center;
  margin-left: 0;
  font-family: 'Typori';
}

.logs {
  display: none;
  position: absolute;
  background-color: #303a52;
  width: 24rem;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
  border-bottom-left-radius: 5px;
  border-bottom-right-radius: 5px;
  border-top-right-radius: 5px;
  border-top-left-radius: 5px;
  padding-top: .75rem;
  padding-bottom: .5rem;
  margin-top: -1.65rem;
  font-family: 'Sax';
}

.logLbl {
  text-align: center;
  color:#f3ecce;
  margin-top: .5rem;
  margin-bottom: .5rem;
  font-family: 'Typori';
  font-size: 114%;
  margin-left: 40%;
  font-weight: bold;
}

.fakeBtn .alertTool {
  visibility: hidden;
  width: 11rem;
  background-color: #3B3A45;
  color: #F7F2DE;
  text-align: center;
  padding: 5px 0;
  border-radius: 6px;
  position: absolute;
  z-index: 1;
  bottom: 101%;
  left: 96%;
  margin-left: -10rem;
  opacity: 0;
  transition: opacity 0.3s;
  font-family: 'Typori';
  font-size: .9rem;
}

.fakeBtn:hover .alertTool {
  visibility: visible;
  opacity: .9;
}

.alertSetup {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: .5rem;
}

.alBtn, .rmAlrt {
  margin-left: 0;
  min-height: 0;
  height: 2rem;
  width: 1.5rem;
  padding: 0;
}

.check {
  width: 1.5rem;
  padding-bottom: 11px;
}

.rmAl {
  width: 1.29rem;
  padding-bottom: 12px;
}

.hidden {
  display: none;
}

.alertLbl {
  color:#F7F2DE;
  font-family: 'Typori';
  padding-right: 4px;
  padding-left: .5rem;
}

.alertLbl a {
  color: #dab367;
  text-decoration: none;
  margin: 0;
  font-size: 100%;
  font-weight: bold;
  border-bottom: 1px dotted #dab367;
}

.priceAlert {
  padding-bottom: 2px;
  text-align: center;
  width: 4.5rem;
  margin-right: .4rem;
  border: none;
  border-radius: 5px;
}

.bell {
  width: 15px;
  margin-bottom: -1px;
}

a {
  margin-left: 1rem;
  margin-right: 1rem;
  font-size: 90%;
}

h4 {
  font-size: 1rem;
  margin-top: .7rem;
  margin-bottom: .7rem;
  margin-left: .7rem;
  color: #f3ecce;
  font-weight: lighter;
}

a:hover {
  color: rgb(195, 195, 195);
  background-color: transparent;
  text-decoration: none;
}
</style>