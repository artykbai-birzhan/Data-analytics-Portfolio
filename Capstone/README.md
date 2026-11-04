# Where does an online store lose its customers?

Capstone project for my Information Systems degree at KBTU. I look at the sales funnel of an electronics store (view, cart, purchase) and try to find the step where most customers drop off.

The work is split in two parts: the analysis and data preparation in Python (`main.ipynb`), and the dashboard in Power BI (`Capstone.pbix`). The slides are in the PDF.

## The question

On which step of the funnel does the store lose the most customers, and where is the biggest room for growth? I set the goal as raising View -> Cart conversion from the baseline of 8.4%.

Metrics I used:

- **View -> Cart %** and **Cart -> Purchase %**: share of sessions that move to the next step.
- **Conversion Index**: conversion of a segment divided by the average conversion. 1.0 means average.
- **Cart Gap**: how many carts a segment would have at the average conversion minus how many it actually has.
- **Observed GMV**: sum of prices of purchase events. This is not revenue, because the data has no discounts, returns or quantities.

## Data

An event log of an online shop selling electronics and home appliances (`events.csv`, event types `view`, `cart`, `purchase`). About 885 thousand events, 407 thousand users, 490 thousand sessions, 53 thousand products, 718 categories and 999 brands. The period is September 2020 to February 2021, and September is incomplete (starts on 24.09).

Dataset link: _add link here_

## What I did

First I cleaned the data. I removed 655 duplicate rows and filled missing `category_code` (26.7% of events) and `brand` (24.0%) with `Unknown`. 162 events had no session, so I left them out of the session analysis.

Prices are very skewed: the median is $65.7, the mean is $146 and the maximum is $64,771. That maximum is one monitor with 4 views and no purchases, so it is an outlier and says nothing about a typical order. Since 99% of events are priced under $890, I used 8 price bands instead of the average price.

The main part is a strict funnel counted by session. A cart only counts if the same session had a view before it, and a purchase only counts if it had both a view and a cart before it. Counting events naively gives 24,344 purchase sessions instead of 20,698, so it overstates purchases by about 18%.

After that I split the funnel by price band, by category and by product (only products with at least 100 views), and made a simple scenario for what happens if each step improves by 0.5, 1 or 2 percentage points. The tables for Power BI are exported from the notebook at the end.

## Results

The funnel in sessions:

| Step | Sessions | Share |
|---|---|---|
| View | 488,360 | 100% |
| Cart | 41,225 | 8.4% of views |
| Purchase | 20,698 | 50.2% of carts, 4.2% of views |

The biggest loss is between view and cart. Only 8.4% of sessions with a view add something to the cart, but about half of the sessions with a cart end in a purchase.

Price bands: the $200-500 band converts best (12.8% View -> Cart, index about 1.5) and brings about half of Observed GMV, around $2.6M out of $5.1M. Items above $1,000 convert at only 2.7-2.8%.

Categories: roughly 30% of views are products without a category, so I removed `Unknown` from the charts. Among the known ones, TV and audio have a lot of traffic but low View -> Cart (4.2% and 6.1%), which gives them the biggest Cart Gap. Video cards are the opposite, 21% at 44 thousand views.

Products: 495 of 908 products with 100+ views convert below the average, and 167 of them (18%) were never added to a cart. Products 775032 and 1674260 have 800-900 views and zero carts, so I would check them first.

Scenario: +1 percentage point on View -> Cart (8.4% to 9.4%) gives about 2,452 extra purchases, which is +11.8% and roughly $0.52M of Observed GMV. The same +1 point on Cart -> Purchase gives only about +2%. So View -> Cart is the better place to work. This assumes Cart -> Purchase stays the same and the average ticket is about $210. It is a scenario and not a forecast, new carts will probably convert worse.

## Recommendations

1. Work on the View -> Cart step: product cards, photos, reviews, availability.
2. Develop the $200-500 segment with assortment and promotions.
3. Look into TV, audio and the products with zero carts.
4. Fix the catalog, since so many views have no category.
5. Test everything with A/B tests before believing it.

## Limitations

Observed GMV is not revenue. A link between price and conversion does not prove that price is the cause, because category and brand matter too. There are only 5 months of data. So all of the conclusions are hypotheses, not proven facts.

## Files

- `main.ipynb`: cleaning, EDA, strict funnel, segments, export of tables (comments in the notebook are in Russian)
- `Capstone.pbix`: Power BI data model, DAX measures and dashboard
- the presentation PDF (in Russian)
- the 8 exported CSV tables: `fact_events`, `fact_sessions`, `dim_product`, `dim_date`, `dim_price_band`, `product_opportunities`, `funnel_by_price_band`, `funnel_by_category`

`events.csv` is not included, download it from the dataset link.

## How to run

```bash
pip install pandas numpy matplotlib jupyter
```

Put `events.csv` next to `main.ipynb` and run all cells. The last cells write the CSV tables and print the funnel counts, which should be 488,360 / 41,225 / 20,698. Then open `Capstone.pbix` in Power BI Desktop. If the file paths are different on your computer, change the sources in Power Query to your CSV files and refresh.
