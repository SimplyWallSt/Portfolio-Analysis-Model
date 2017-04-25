Simply Wall St Portfolio Analysis Model
=======================================

Overview of the model
---------------------

The Simply Wall Street (SWS) app is designed to help make you a better investor by allowing you to make non-emotional long term investment decisions. It is recommended you read our [Company Analysis Model](http://github.com/SimplyWallSt/Company-Analysis-Model/blob/master/MODEL.markdown) documentation before this, as it is based upon the results of that analysis.

For many investors their Portfolio is nothing more than a list of stocks with positive or negative returns. The aim of the SWS Portfolio infographic report is to improve the users understanding of their Portfolio and therefore make better decisions by:

-   Understanding what kind of Portfolio they currently have;

-   Realization of their Portfolio value versus the price;

-   Understanding of the individual companies that make up their Portfolio;

-   Understanding their returns relative to a benchmark (e.g. the market or another Portfolio).

We encourage users to decide upon and following a strategy once equipped with the information and tools provided by SWS.

To assist in this process Simply Wall St is able to analyse a Portfolio of stocks based on the results of our analysis of the individual companies and an analysis of returns.

The differences between a Watchlist, Holdings and Portfolio
-----------------------------------------------------------

A Watchlist is a Portfolio without any tractions or value associated with the holdings. A Holdings Portfolio is a Watchlist with a number of shares assigned to each holding, a bit like a weighted Watchlist and finally a Portfolio has full transaction detail.

To calculate returns on Watchlists and Holdings we create one Buy transaction per Holding for the period selected.

### Watchlists

We back calculate the original number of shares in the Buy transaction so that the final value of each holding is equally weighted.

### Holdings

We use the number of shares assigned to each stock or holding for the Buy transactions.

### Portfolio

We account for all recorded transactions.

The Portfolio Snowflake
-----------------------

The Portfolio Snowflake is calculated from the weighted average of the individual Snowflakes that make up the Portfolio. ETFs and Funds are ignored from this.

### Best and Worst Contributor

The best and worst contribute to each score on the Portfolio Snowflake is calculated by:

    Contributor value = Score \ Weighting

The Best (Highest) and Worst (Lowest) scores from each holdings are the contributors.

Portfolio Return Calculation
----------------------------

Simply Wall St uses the dollar-weighted (aka money-weighted) method to calculate Portfolio returns where applicable.

This method measures investment performance taking account of the size and timing of cash flows. For individual investors who have control of their accounts the dollar-weighed calculation is recommended as the more appropriate method. The alternate method is the time-weighted return which is typically used by fund managers who cannot control when new funds are deposited or removed from their accounts.

To calculate the dollar-weighed return:

1.  The average investment period (average years invested, AYI) is calculated by weighting the length of time that each capital input (e.g. Buy) was invested for;

2.  The Simple Total Return is the gain divided by the average years invested;

3.  The Annualised growth rate is the annual gain per year required to achieve the total gain.

Note: if the AYI is less than 1 year no Annual growth rate is provided as this number is meaningless. An example of this would be short term volatility extrapolated over a year.

### Example Dollar-Weighted Return Calculation

We start with the output from the SWS Returns Report for comparison, note this example uses Capital Gains only.

    **Simply Wall St Calculation Report**						
							
    Ticker		Transaction Type	Date		Price/Amount	Shares	Bought		Sold		Years
    Nasdaq:AMZN	Buy			1/05/2013	$248.23		10	$2,482.30	-		3.39
    Nasdaq:AMZN	Buy			19/01/2016	$571.77		5	$2,858.85	-		0.67
    Nasdaq:AMZN	Sell			9/05/2016	$679.75		-10	-		-$6,797.50	
    Totals										$5,341.15	-$6,797.50	1.93
						
    Current Position							
    Net original cost	Total shares	Current Price	Current Value	Capital Gain
    -$1,456.35		5		$778.52		$3,892.60	$5,348.95
    
    Total Return: 100.15%	


    **Dollar-Weighted Return Example Calculation**		
    Gain 	= Total Gain from Sales + Current Value - Total Bought
    $5,348.95	=$6,797.50		+ $3,892.60	- $5,341.15

    Return  = Total Gain / Total Capital Invested
    100.15% = $5,348.95	 / $5,341.15
     
     
    **Compound Annual Growt Rate (CAGR) Example**		
    CARG   = ( 1 + Total Return ) ^ ( 1 / Avg. Years) - 1		
    43.33% = ( 1 + 1.0015 ) ^ ( 1 / 1.93 ) - 1
    
    
    **Comparison to Common Broker Method**	
    Avg Cost of Current Holding = Total Shares * Weighted Avg. Buy Price	
    $1,780.38                   = 5			   * $356.08

    Return   = ( Current Value - Average Cost ) / Average cost		
    118.64%  = ( $3,892.60 - $1,780.38    ) / $1,780.38






### Corporate Actions

Regardless of Portfolio type any corporate actions are included.

#### Dividends

Any dividends paid are included in the returns calculation.

If the option for dividend reinvestment is selected then any dividends paid are converted into the equivalent number of shares on the day of the action.

### Dividend Reinvestment
Dividends can be reinvested on a per stock basis. This converts any dividend payments to an equivalent fractional share purchase on that day at 0 cost.

#### Splits

Any stock splits (or consolidations) are included in the returns calculation. If a stock split results in a fractional share this is rounded up the nearest whole number of shares, as per common practice.

### Currency Conversion

If a stock is held in a different currency to that of the Portfolio then conversions are done based on end of day prices on:

-   Any Buy or Sell transactions
-   The current value of the Portfolio + the current value of any dividend payments which have not been reinvested

#### Example Currency Conversion Calculation
    **Example currency conversion calculation**
    						USD			EUR			Exchange Rate
    Buy 100 shares @ $10	$1,000 	 	€1,400 		1.4
    Current Value	 		$1,200 	 	€1,800 		1.5
			
    Gain from Currency		 			€100 	
    Gain from Price	 		$200 	 	€280 	
			
    Currency gain from Capital Gain		€20 	
			
    Combined gain		 				€400 
    
    Current Value of original gain							€300 (1.5 x $200)
    Net Currency Gain (Difference of combined - original) 	€100

    


Remaining Portfolio Data
------------------------

The remaining Portfolio data such as Value, Future etc is calculated from the weighted average of the individual company results (e.g. PE Ratio). We impose fair limits on the various metrics to ensure extremely outlier do not skew the result, an example being a stock with a PE ratio of 2000x.

The following exceptions/ notes are made:

### Volatility

Unlike all the other Portfolio data ETF’s and funds are included in the Volatility calculation which uses the average 5 year Beta value weighted by current holding value.

### Value

#### Portfolio Intrinsic Value based on Free Cash Flows

To calculate the Intrinsic Value of the Portfolio the sum of individual Intrinsic values for each holding are multiplied by the number of shares held.

For some smaller market cap companies, or financial firms, we are sometimes unable to calculate an intrinsic value. Shares in these companies are ignored in the calculations and for this reason the total value is sometimes lower than that of the total Portfolio value.

#### PE, PEG and PB market ratios

When calculating the weighted average for the Portfolio any companies with negative ratios are ignored.

### Future Performance

Companies that are missing analyst consensus estimates for future growth are ignored from the weighted average of 1 and 3 year earnings growth.

### Health

Banks and finance firms are ignored when calculating the weighted average debt to equity ratio.
