# Exercises: Using with Trading APIs: Bitstamp, Bitfinex, Coinbase and Kraken

The goal of this exercise is to consume trading **APIs** and get
**prices** and **orders** from the **orderbook** from various exchanges
like Bitstamp, Bitfinex, Coinbase and Kraken. An API is an "application
program interface", usually provided for external access through RESTful
Web Services, JSON-RPC or other communication protocol. It basically
provides an access to company's data that isn\`t traditionary setup in
the way that may be in the website.

Our example will use public data functions, which **exchanges** offers
without registration through their **public APIs**. We will use
"**Python 3"**.

For this exercise we use **Ubuntu 16.04.3**. Also, you will need
\"**Python3**\" installed.

Create the Trading API Project
------------------------------

1.  Open command terminal and create working directory for example
    "**ExerciseAPI**". Enter in the new created directory.

![](/assets/exercises-trading-apis-01.png)

2.  Create new file. Name it "**ExerciseAPI.py**". In first row we
    imported **time**, **json** and **request**.

![](/assets/exercises-trading-apis-04.png)

3.  Before continue further let\`s see what is exchanges APIs look like.
    Open **<https://www.bitstamp.net/api/>** and have a look on **public
    data functions**.

![](/assets/exercises-trading-apis-05.png)

4.  For example let\`s open **<https://www.bitstamp.net/api/ticker/>**
    It contains text in json format. In our API we will get info from
    this jsons.

> ![](/assets/exercises-trading-apis-06.png)

5.  In the same logic you can take info about BTCUSD (or another pair)
    **order book** from
    <https://www.bitstamp.net/api/v2/order_book/BTCUSD/>
    ![](/assets/exercises-trading-apis-07.png)

6.  Now let\`s get info from bitstamp **ticker**. Here we use **last**
    and with response it will give us **last BTC price** but you can
    experiment with other values for example **volume** will give you
    **Last 24 hours volume**.

    ![](/assets/exercises-trading-apis-09.png)

8.  With similar logic let\`s get last prices from other exchanges like
    **bitfinex**, **coinbase** and **kraken**.

    ![](/assets/exercises-trading-apis-010.png)

9.  Now let\`s get some info from bitstamp **order book**. The
    difference is that in this case API returns a JSON dictionary with
    \"bids\" and \"asks\". Each is a list of open orders and each order
    is represented as a list holding the price and the amount.

    ![](/assets/exercises-trading-apis-07.png)

10. Here is the code that gets price and quantity for last bid and ask
    orders.

    ![](/assets/exercises-trading-apis-011.png)

11. It only remains us to print the info and update it in every 3
    seconds.

    ![](/assets/exercises-trading-apis-02.png)

12. Let\`s start the program. Type in console:

  \$ python3 ExerciseAPI.py
  --------------------------------
  Windows: python ExerciseAPI.py

![](/assets/exercises-trading-apis-03.png)

You can find the whole code in
<https://github.com/SMandazhiev/TradingAPI/blob/master/ExerciseAPI.py>

Follow the Described Steps
--------------------------

Your task is follow the tutorial described above and create the trading
API.

1.  Create the API.

2.  Experiment and try to get different data.

3.  Try to get info from different sources.

What to Submit?
===============

Create a **zip file** (e.g. **your-name-trading-api-exercise.zip**)
holding the screenshots with your experiments. Make screenshots of code
and terminals.

Submit your **zip** file as **homework** at the course Web site.
