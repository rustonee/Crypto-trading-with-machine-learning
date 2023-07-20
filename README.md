Crypto Trading Algorithm
This project is a cryptocurrency trading bot developed using Machine Learning and Rust. It draws inspiration from CyberPunkMetalHead/cryptocurrency-machine-learning-prediction-algo-trading.

:warning: Disclaimer
Please note that this bot was created as a response to another project and out of personal curiosity to build an improved version in Rust. The effectiveness of the trading strategy itself has not been extensively tested. Therefore, use this program at your own risk!

:book: Strategy
The trading strategy employed by the bot is relatively straightforward:

Retrieve the most recent X days of hourly kline (candle) data from Binance.
Train a machine learning model using the data. In this case, LightGBM is utilized, which is a fast gradient boosting framework that employs tree-based learning algorithms. While it may not be as accurate as other solutions like recurrent neural networks (RNN) such as LSTM, it has proven to be a reliable indicator for basic market movements (price increase or decrease) in testing, which is sufficient for this strategy.
Utilize the trained model to predict the current candle's high price. If the predicted price is lower than the current open or close price, the bot waits for the next candle and repeats the process. Otherwise, it places a buy order.
Finally, the bot waits for the price to rise until the predicted value is reached. If the prediction is not met by the end of the candle, it continues to wait until the prediction is eventually fulfilled.
💻 Installation & Usage
To get started, install Rust and clone this repository:

$ git clone https://github.com/sleeyax/ml-crypto-trading-bot.git
$ cd ml-crypto-trading-bot
Copy
Next, copy the configuration file and make the necessary edits (the file should be self-explanatory):

$ cp config.example.yaml config.yaml
$ vim config.yaml # or use any other text editor of your choice to modify the config file
Copy
To run the bot in development mode, execute:

$ RUST_LOG=debug cargo run
Copy
To run the bot in production mode, execute:

$ RUST_LOG=info cargo run
Copy
You can also build a release binary using cargo build -r and copy it, along with your config file, to a VPS or Raspberry Pi.

📷 Screenshots
Screenshot