# BTC Conky
### *getbtc - скрипт для вывода стоимости криптовалют на монитор Conky*

 Скрипт для формирования стоимости валют и изменения их стоимости течении 1 часа и в течении 24 часов
```shell
 1 колонка - Символ валюты;
 2 колонка - Стоимость валюты в $;
 3 колонка - изменение стоимости в течении 1 часа;
 4 колонка - изменение стоимости в течении 24 часов;
```
 Скрипту необходимо передать параметр идентификатор валюты, который можно узнать на [CoinMarketCap](https://api.coinmarketcap.com/v1/ticker/)

 Для работы скрипта необходимо становить утилиту `jq`
```shell
 apt install jq
```
Например:
```json
{
        "id": "bitcoin", 
        "name": "Bitcoin", 
        "symbol": "BTC", 
        "rank": "1", 
        "price_usd": "8942.67", 
        "price_btc": "1.0", 
        "24h_volume_usd": "10282800000.0", 
        "market_cap_usd": "150618931576", 
        "available_supply": "16842725.0", 
        "total_supply": "16842725.0", 
        "max_supply": "21000000.0", 
        "percent_change_1h": "1.76", 
        "percent_change_24h": "10.07", 
        "percent_change_7d": "-20.41", 
        "last_updated": "1517657669"
    }
```
Запуск скрипта `./getbtc bitcoin`

Пример как отобразить некоторые валюты в Conky
```lua
conky.text = [[
...
$hr
 $color ${execi 30 getbtc bitcoin}
 $color ${execi 30 getbtc ethereum}
 $color ${execi 30 getbtc ethereum-classic}
 $color ${execi 30 getbtc zcash}
 $color ${execi 30 getbtc zclassic}
 $color ${execi 30 getbtc zencash}
 $color ${execi 30 getbtc bitcoin-gold}
 $color ${execi 30 getbtc bitcoin-cash}
 $color ${execi 30 getbtc monero}
 $color ${execi 30 getbtc monacoin}
 $hr
...
```

