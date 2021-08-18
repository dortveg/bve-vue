# WORK IN PROGRESS

ongoing conversion to vue, see vanilla js repo [here](https://github.com/dortveg/bve)

# Big Volume Energy

BVE is a cryptocurrency price and volume ticker/tracker with alerts.

## Usage

Simply type in your desired coin pairs without any spaces, dashes or slashes (ex. "BTCUSDT") and turn it on.\
BVE will show the current price and 24hr change as a ticker. It will also update and show the volume flow for every set interval (default 1 minute), and compare it to the average volume flow for the past 3 hours.\
Whenever the current volume flow is higher than the average volume flow by your desired amount (default 100%), BVE will play a sound alert and show each event in the notifications dropdown. You can also turn off the sound if you wish and just receive the notifications.\
\
Currently it receives the price and volume data from Binance.com only. 

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

## License
[GNU AGPL](https://choosealicense.com/licenses/agpl-3.0/)
