# CoinWatch - Real-Time Cryptocurrency Price Ticker

(upcoming project: 2025)

CoinWatch is a real-time cryptocurrency price tracking application designed to display the latest crypto prices on a Flask web dashboard or an OLED screen connected to a Raspberry Pi. With alert functionality for significant price changes, CoinWatch helps you stay updated on your favorite cryptocurrencies.

---

## Features
- **Real-Time Price Tracking**: Get up-to-the-second prices of selected cryptocurrencies from the CoinGecko or Coinbase API.
- **Price Alerts**: Receive alerts for significant price changes (spikes or drops) to assist with trading decisions.
- **Multi-Platform Display**: View prices on an OLED screen connected to a Raspberry Pi or a web dashboard powered by Flask.
- **Customizable Coin Selection**: Track the coins that matter most to you, and easily adjust the list of displayed cryptocurrencies.
- **Easy to Use**: Simple setup with clear instructions for installation and configuration.

---

## Table of Contents
1. [Installation](#installation)
2. [Configuration](#configuration)
3. [Usage](#usage)
4. [Screenshots](#screenshots)
5. [Future Enhancements](#future-enhancements)
6. [Contributing](#contributing)
7. [License](#license)

---

## Installation

### Prerequisites
- **Raspberry Pi 400** or other Raspberry Pi models (for OLED display setup)
- **Python 3.7+**
- **Pip** (Python package manager)
- **CoinGecko or Coinbase API Key** (if required)
- **Flask** and **GPIO Libraries** (for display on Flask or OLED)

### Steps
1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/CoinWatch.git
   cd CoinWatch
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up API access**:
   - Register on [CoinGecko API](https://www.coingecko.com/en/api) or [Coinbase API](https://www.coinbase.com/) and obtain your API key (if necessary).
   - Save the API key in a `.env` file:
     ```
     API_KEY=your_api_key_here
     ```

4. **Connect the OLED Screen** (optional):
   - Follow instructions to wire the OLED to your Raspberry Pi GPIO pins.
   - Install the necessary GPIO libraries for Python:
     ```bash
     pip install adafruit-circuitpython-ssd1306
     ```

---

## Configuration

1. **Choose Cryptocurrencies**:
   - In the configuration file (`config.json`), add the symbols of the cryptocurrencies you want to track (e.g., BTC, ETH, DOGE).
   
   ```json
   {
       "cryptos": ["BTC", "ETH", "DOGE"],
       "price_alert_threshold": 5  // Alert if price changes by 5%
   }
   ```

2. **Set Alert Thresholds**:
   - Define your price alert threshold in `config.json`. This value represents the percentage change that will trigger an alert.

---

## Usage

### Start the Dashboard
To start the Flask web dashboard:
```bash
python app.py
```
- Open your browser and go to `http://localhost:5000` to view the price dashboard.

### OLED Display
To show prices on an OLED screen:
```bash
python display.py
```
- This command fetches data and displays prices on the OLED connected to your Raspberry Pi.

### Alerts
- Alerts for significant price changes will show up as notifications on the dashboard or OLED screen. Modify thresholds in `config.json`.

---

## Screenshots

### Web Dashboard
![CoinWatch Web Dashboard](screenshots/dashboard.png)

### OLED Display
![CoinWatch OLED Display](screenshots/oled_display.png)

---

## Future Enhancements
- **Email/SMS Alerts**: Option to send alerts directly to your phone or email.
- **Historical Price Trends**: View price changes over time in the dashboard.
- **Additional Coin Data**: Include more stats like market cap, volume, and percentage change over time.
- **Multiple Display Modes**: Option to switch between simple ticker and full stats on the OLED.

---

## Contributing
We welcome contributions! Please open an issue or submit a pull request for improvements and suggestions.

1. Fork the repository.
2. Create your feature branch: `git checkout -b feature/YourFeature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/YourFeature`
5. Open a pull request.

---

## License
Distributed under the MIT License. See `LICENSE` for more information.

---

Stay up to date with your favorite cryptocurrencies anytime, anywhere, with **CoinWatch**! 🚀
```
