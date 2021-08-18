<template>
  <footer>
    <p class="disclaimer">BVE only aims to be a helpful tool. The user assumes responsibility for all their financial actions and subsequent consequences.</p>
    <div class="sig">
      <div class="expandDonate">
        <button class="donateBtn">Donate</button>
        <div class="donateInfo">
          <span class="plea">If you love BVE, please show your support and help make it bigger and better!</span>
          <hr class="ihr">
          <h6>BTC: 1JZEk5FkuTGLWpMdgzXH3AHfqohXaqyFsZ</h6>
          <h6>ERC20: 0xcfC8D2e358F656440C8628722fA850cB12245D31</h6>
          <h6>NANO: nano_37n6z9gqs1j73pwq3gzswegdyk8haty1pifu7obk9eftutxujzer6n5j7kkp</h6>
          <h6>XMR: 49j14X3nqN74eqDkVLKiARjJsXC4EZHLWKZsg6HMwntLXAhHH6J75GeBpevKaS8NZ956cb43KsUKbh9KAjuJugzA7RNKhhU</h6>
        </div>
      </div>
      <span class="copyright">~ ©2021 GT ~<a class="link" href="https://github.com/dortveg">GitHub</a></span>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style>
footer {
  background-color: #3B3A45;
  text-align: center;
  padding-top: .3rem;
  padding-bottom: .7rem;
  margin-top: 2.7rem;
  border-top-left-radius: 9px;
  border-top-right-radius: 9px;
  font-family: 'Typori';
}

.sig {
  padding-top: .5rem;
  margin-right: .5rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.disclaimer {
  font-size: 1rem;
  color: #131420;
  padding-bottom: 0;
  padding-top: .8rem;
}

.expandDonate {
  position: relative;
  display: inline-block;
  width: 5rem;
  margin-right: 2px;
}

.expandDonate:hover .donateInfo {
  display: inline-block;
}

.donateBtn {
  color: #212444;
  font-size: 1rem;
  font-family: 'Typori';
  width: 5rem;
  min-height: 2rem;
  margin-left: 0;
  margin-top: 1px;
  padding: 0;
}

.donateInfo {
  display: none;
  position: absolute;
  background-color: #303a52;
  color: #f3ecce;
  width: 43rem;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
  border-bottom-left-radius: 5px;
  border-bottom-right-radius: 5px;
  border-top-right-radius: 5px;
  border-top-left-radius: 5px;
  padding-top: .75rem;
  padding-bottom: 1rem;
  margin-top: -5.2rem;
  font-family: 'Typori';
}

.plea {
  font-size: .95rem;
}

h6 {
  margin: 4px 0 0 0;
  font-family: 'Sax';
  font-size: .75rem;
}

.copyright { 
  color: grey;
  font-size: 1.1rem;
}

.link:link, .link:visited {
  color: #212444;
  background-color: transparent;
  text-decoration: none;
}

.link:hover {
  color: grey;
  background-color: transparent;
  text-decoration: none;
}
</style>