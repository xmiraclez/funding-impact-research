# Bitcoin negative funding and the fear and greed index

The notebook recomputes the post about next-day BTC returns on days of extreme fear, extreme greed, and negative funding.

Run `funding_fear_greed.ipynb` from top to bottom. Dates and thresholds live in the first code cell.

The post text is still computed on 21 January 2020 through 9 September 2024 and matches the screenshot: t and p are −0.32 and 0.75 for fear, 1.2 and 0.22 for greed, and 2.1 and 0.035 for negative funding. The mean next-day returns in that text are 0.75% and 0.09%.

After the data load, the same four conditions are studied three times, each in its own section: the original window, the stretch from 10 September 2024 through the last available day, and the full history. Each section has its own t-test tables, its own return histograms, and its own charts. The three windows are not drawn on one figure. `END = None` reads data through the end of the Binance archive.

The greed threshold in this calculation is an index strictly above 70. The screenshot caption “index > 80” does not produce these figures.

This is not investment advice.

## Data sources

- Price: daily BTC-USD close, Yahoo Finance.
- Fear and greed index: [alternative.me](https://api.alternative.me/fng/).
- Funding: public monthly archives of Binance USD-M `BTCUSDT`, the last 8-hour print of each UTC day. That is the same sign and the same series the old notebook stored as the Coinalyze close. No Coinalyze key is required.

If the network is unavailable, the notebook reads the snapshots in `data/`.

## Run locally

Python 3.11 or newer.

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

Open `funding_fear_greed.ipynb` and choose Run All.

Run without the interface:

```bash
python3 -m jupyter nbconvert --to notebook --execute --inplace funding_fear_greed.ipynb
```
