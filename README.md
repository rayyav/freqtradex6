# Crypto Bot

[Freqtrade](https://www.freqtrade.io/en/stable/) Crypto Bot with [NostalgiaForInfinity](https://github.com/iterativv/NostalgiaForInfinity) Strategy.<br>
*The strategy is constantly updated from a Github Action.*

## Getting Started

If not already done, install [Docker](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/other/)

**Clone repository**
```bash
git clone https://github.com/rayyav/freqtradex6.git && cd crypto-bot
```
**Generate the private configuration file**
```bash
cp templates/config.private.json.template user_data/config.private.json
```
**Start Crypto Bot.** *(By default the mode is enabled **Dry-Run**)*
```bash
docker-compose up -d
docker-compose up -d
docker compose logs -f.
chown -R 1000:1000 user_data
```
To access FreqUI go to `http://localhost:8080/` and register a new bot with the username and password that indicates the `config.private.json` ***(You can change it at any time)***. In the same file you can activate telegram notifications, configure the exchange credentials and disable dry-run mode.


## Automatically Update Crypto Bot

```bash
cp templates/update-crypto-bot.sh.template scripts/update-crypto-bot.sh
cd ${HOME}/crypto-bot/scripts
# In update-crypto-bot.sh, add TG_TOKEN, TG_CHAT_ID and confirm the CRYPTO_BOT_PATH (Path where you cloned your project)
chmod -x active-crontab.sh && ./active-crontab.sh
```


## Backtesting

If not already done, install Make: `sudo apt install make`<br>
*Note: All parameters are optional, I could see their default value in the [Makefile](https://github.com/kerycdiaz/crypto-bot/blob/main/Makefile)*

**Download the pairs you need to perform backtesting**
```bash
make download-data EXCHANGE=binance TIMERANGE=20220101-20220201 TIMEFRAME='5m'
```

**Know the downloaded pairs and their temporality**
```bash
make list-data EXCHANGE=binance
```

**Running backtesting for a defined strategy**
```bash
make backtesting EXCHANGE=binance STRATEGY=SampleStrategy TIMERANGE=20220101-20220201 TIMEFRAME='5m'
```

***If you want to backtest the `NostalgiaForInfinityX` strategy you must download the data for `'5m 15m 1h 1d'`***
____
## Disclaimer

This is a personal experimentation software. Do not risk money which
you are afraid to lose. USE THE SOFTWARE AT YOUR OWN RISK. THE AUTHORS
AND ALL AFFILIATES ASSUME NO RESPONSIBILITY FOR YOUR TRADING RESULTS.
____

## Credits

Created by [Keryc Díaz](https://www.linkedin.com/in/kerycdiaz/), NostalgiaForInfinity maintained by [Iterativ](https://github.com/iterativv).
