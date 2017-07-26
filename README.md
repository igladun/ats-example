# Automated Trading System example

That ATS is using XChange library for interaction with cryptocurrency exchanges. It is taking btc price from Bitfinex, 
Bitstamp, Kraken, and comparing it with DSX price. If it satisfies the condition, then place an order to buy bitcoin 
on dsx.uk. If better price appears in order book, then cancel existing order and place new order with better price.

#### How to use ATS
For using this ATS you can run sh scripts. 
1) You have to give permissions to scripts. Run:  

    1) chmod +x buildAts.sh
    2) chmod +x startAts.sh
    3) chmod +x shutdownAts.sh
2) Run buildAts.sh. This script will create jar file.
3) If you want to launch ATS, then run startAts.sh.
4) If you want to stop ATS, then run shutdownAts.sh.
#### Config and rateLimit json files usage
Files config.json and rateLimit.json in ats-example are used for AtsMain class. Files config.json and rateLimit.json in 
ats folder are used for AtsAlgoTest class, i.e. for testing purposes.
#### Clarification of config.json
        "url" : dsx.uk api address. Can be changed, that's why it's in properties.
        "secretKey": your account secret key,
    
        "apiKey": your account public key,
  
        "pricePercentage": percentage, for which multiply dsx price bid order for condition checking. 
        For example - "1.01" will check if bid order average bigger than dsx bid order * 1.01,
   
  
        "priceScale": number of decimals after dot for price, e.g. 5,
  
        "volumeScale":  number of decimals after dot for volume, e.g. 4,
  
        "priceAddition": addition for order price, for example "0.01" - 1 cent,
  
        "averagePriceUpdateTime": how often to update average price in milliseconds, e.g. - 3000
  
        "timestampForPriceUpdate": timestamp in seconds for condition if current price timestamp less 
        than X seconds, than don't use this price for calculating average, e.g. - 3
  
        "dsxAccountType": type of dsx account, e.g. - "LIVE" or "DEMO"
  
        "stepToMove": step for order movement. If price in orderbook bigger than that step, cancel order 
        and place order with new price, e.g. - "0.01"
  
        "volumeToMove": "0.05" volume for order movement. If volume before user's order in order book 
        bigger than volumeToMove, cancel order and place order with new price
        "waitingTimeForOrderCheck": time for checking order status after it was placed.
    
#### Clarification of rateLimit.json
        
        "Exchange" - time in seconds to set how often price from exchange should be taken