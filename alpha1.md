----------------------------------------------

-rank(ebit / capex)

Equity	USA	TOP3000	Fast Expression	0	1	0.08	Subindustry

----------------------------------------------

ts_zscore(mdf_yld,20)

Equity	USA	TOP3000	Fast Expression	3	1	0.99	Sector	On	Off	Verify

----------------------------------------------

((-1 * rank((delta(close, 3) * (1 - rank(decay_linear((volume / adv20), 9)))))) * (1 + rank(sum(returns, 2650))))

Equity	USA	TOP3000	Fast Expression	2	1	0.12	Industry	On	Off	Verify

----------------------------------------------

-rank(close / open-0.05)*1.011

Equity	USA	TOP3000	Fast Expression	16	1	0.21	Subindustry	On	Off	Verify

----------------------------------------------

ts_av_diff(mdf_nps,500)

Equity	USA	TOP3000	Fast Expression	4	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

rank(mdf_rds)
Equity	USA	TOP500	Fast Expression	10	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

alpha = -group_rank(fnd2_ebitdm, industry)-group_rank(fnd2_ebitfr, industry);
group_rank(fn_assets_fair_val_a,industry)>0.5?alpha*2 : alpha

Equity	USA	TOP500	Fast Expression	4	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

ts_arg_max((income - mdf_tax - dividend)/(sharesout),6)

Equity	USA	TOP3000	Fast Expression	20	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

group_rank(fam_est_eps_rank, sector)

Equity	USA	TOP200	Fast Expression	5	1	0.04	Market	On	Off	Verify

----------------------------------------------

group_vector_neut(rank(-mdl175_volatility* log(volume))*(1+group_rank(mdl175_revenuettm,sector)),ts_mean(mdl175_02amvt,240),sector)

Equity	CHN	TOP3000	Fast Expression	3	1	0.01	Market	On	Off	Verify

----------------------------------------------

call_breakeven_10/put_breakeven_10

Equity	USA	TOP1000	Fast Expression	4	1	0.01	Subindustry	On	Off	Verify

----------------------------------------------

(rank((vwap - ts_min(vwap, 20))) < rank(correlation(vwap, ts_mean(volume, 40), 90)))

Equity	USA	TOP3000	Fast Expression	4	1	0.08	Industry	On	Off	Verify

----------------------------------------------

market_ret = ts_product(1+group_mean(returns,1,market),250)-1;
rfr = vec_avg(fnd6_newqeventv110_optrfrq);
expected_return = rfr+beta_last_360_days_spy*(market_ret-rfr);
actual_return = ts_product(returns+1,250)-1;
// #group_rank(actual_return-expected_return, subindustry)
actual_return-expected_return+volume

Equity	USA	TOP1000	Fast Expression	5	1	0.01	None	On	Off	Verify


----------------------------------------------

# tiền lãi * số cổ hiếu - doanh thu
group_rank(interest_expense*count(sharesout)-revenue, market)   

Equity	USA	TOP500	Fast Expression	10	1	0.08	None	On	Off	Verify

----------------------------------------------

rank((cash+sales_growth-sales_ps)/debt_lt)

Equity	USA	TOP200	Fast Expression	10	1	0.1	Market	On	Off	Verify

----------------------------------------------

rank(-ts_returns(max(close, vwap), 2)*(count(sharesout)/volume))

Equity	USA	TOP500	Fast Expression	10	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

a = rank(sales / assets) + rank(count(sharesout)/volume);
ts_delta(-a, 251)

Equity	USA	TOP3000	Fast Expression	10	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

a = enterprise_value/ebit;
b = cash/cashflow_op;
c = current_ratio;

trade_when(a<=8.1, rank(exp(-ts_mean(a-log(b)-log(c),21))),-1)

Equity	USA	TOP3000	Fast Expression	5	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

group_rank(trade_when(close>ts_delay(close,21),-ts_av_diff((mdf_eno),3500),-1),industry)

Equity	USA	TOP500	Fast Expression	4	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

-ts_av_diff(mdf_qe2,1700)

Equity	USA	TOP500	Fast Expression	4	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

group_rank(ts_regression(log(mdf_ccr/2),call_breakeven_1080,221,rettype=2),market)

Equity	USA	TOP200	Fast Expression	4	1	0.08	Sector	On	Off	Verifty

----------------------------------------------





----------------------------------------------
