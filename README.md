# IndiaVIX-implementation

# Assumptions & procedures followed to implement this:-


1.   Taking first 10 strikes for near month and first 5 strikes for next month options expiration contracts as we're not given bid-ask spread data. The near-month expiry are more liquid therefore included more range in them upto ten strikes on both CE & PE side
2.   Strikes of only a multiple of 100 are taken as they're generally more liquid and have more values/data-points compared to the ones that are 50 units away
3. Monthly rolling data isn't considered for simplification and therefore each iteration computes monthly Vix values which can then be merged together. Moreover the near-month expiry files have data beyond the expiry date which ideally shouldn't be the case as after expiry the Futures contracts seize to be publicly available for trading.
4. As I've fixed the strike interval, therefore delta_Ki as described in the whitepaper is also fixed to a value of 100 i.e., difference between two consecutive strikes that are 100 units apart.
5. Right now, the vix value is computed for every 5 min-interval(to prevent more data resources usage and reduction in time to compute vix) and if both near and next month sigma values are available then only for that particular time the vix is computed else ignored. The time-interval can be changed easily for more precision in calculation frequency.
6. The variable names are almost identical to closely resemble whitepaper. The procedures/functions are first presented in this colab notebook followed by the main execution block at the end.
7. The input_path governs the path for the folder containing data files, which can be changed whereever it's running. I ran it on Google Colab and files were stored in Google-Drive.
8. To improve efficiency, only the data files which have same expiry as was required were loaded and read.
9. The sigma for both near & next-month expiry was calculated to get the final India VIX value. The methodology except these above assumptions were almost to identical as was described in the whitepaper.
