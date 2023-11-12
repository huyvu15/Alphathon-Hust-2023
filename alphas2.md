----------------------------------------------
rank(ts_delta(debt/assets,360))

Instrument Type	Region	Universe	Language	Decay	Delay	Truncation	Neutralization	Pasteurization	NaN Handling	Unit Handling
Equity	USA	TOP3000	Fast Expression	4	1	0.08	Market	On	Off	Verify

----------------------------------------------

rank(-ts_delta(rating*implied_volatility_mean_1080*cap, 360))
/# rank(-ts_delta(rating*news_max_dn_amt*cap, 360))

Equity	USA	TOP500	Fast Expression	3	1	0.5	Subindustry	On	Off	Verify

----------------------------------------------

-max(rank(vwap/open) ,rank((low/high)))

Equity	USA	TOP3000	Fast Expression	6	1	0.1	Subindustry	On	Off	Verify

----------------------------------------------

rank(-fam_roe_rank*count(sharesout)+volume/assets)
Equity	USA	TOP200	Fast Expression	12	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

/# (sales_ps < last_diff_value(volume,3)?1:rank(ts_delta(vwap,3)))
ts_sum(rank(volume/assets) + rank(sales_growth/ebit),2)

Equity	USA	TOP3000	Fast Expression	4	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

-ts_rank((((high * low)*0.1) - max(vwap,close)*max(count(sharesout), count(employee))),2)

Equity	USA	TOP1000	Fast Expression	15	1	0.1	Subindustry	On	Off	Verify

----------------------------------------------

-rank((-1 * ((1 - (return_assets / debt_lt)))))

Equity	USA	TOP1000	Fast Expression	15	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

-correlation_last_90_days_spy*rank( 1/(open/vwap))

Equity	USA	TOP1000	Fast Expression	10	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

/# sign(ts_covariance(mdl175_variance20+mdl175_zid, mdl175_ysp, 22))
sign(ts_covariance(mdl175_variance20+sqrt(mdl175_zid)+vwap, mdl175_ysp*sharesout/volume, 19))

Equity	CHN	TOP3000	Fast Expression	10	1	0.1	Subindustry	On	Off	Verify

----------------------------------------------

rank(mdl175_totalfixedassets*vwap^1.035/volume)*1.111 + rank(sqrt(sharesout)/volume)*1.37 + rank(close/open*high/low)*1.652

Instrument Type	Region	Universe	Language	Decay	Delay	Truncation	Neutralization	Pasteurization	NaN Handling	Unit Handling
Equity	CHN	TOP2000	Fast Expression	4	0	0.2	Subindustry	On	Off	Verify


----------------------------------------------

dk = ts_covariance(debt, assets, 22);
-trade_when(dk, rank(capex/ebit), -1)

Instrument Type	Region	Universe	Language	Decay	Delay	Truncation	Neutralization	Pasteurization	NaN Handling	Unit Handling
Equity	USA	TOP3000	Fast Expression	10	1	0.08	Subindustry	On	Off	Verify


----------------------------------------------

alpha = -group_rank(fnd2_ebitdm, industry)-group_rank(fnd2_ebitfr, industry);
group_rank(pv13_com_page_rank,industry)>0.5?alpha*2 : alpha

Instrument Type	Region	Universe	Language	Decay	Delay	Truncation	Neutralization	Pasteurization	NaN Handling	Unit Handling
Equity	USA	TOP500	Fast Expression	10	1	0.08	Subindustry	On	Off	Verify


----------------------------------------------

sum_vol = ts_sum(vec_sum(scl12_alltype_buzzvec), 5);
significance = vec_norm (scl12_alltype_sentvec) / vec_count(scl12_alltype_sentvec);
sent_vol = -ts_rank(sum_vol, 65);
sent_sig = ts_max(significance, 10);
sent_vol * group_rank(sent_sig, sector)

Instrument Type	Region	Universe	Language	Decay	Delay	Truncation	Neutralization	Pasteurization	NaN Handling	Unit Handling
Equity	USA	TOP200	Fast Expression	0	1	0.01	Market	On	Off	Verify


----------------------------------------------

-sign(close^0.550075-vwap^0.55)

Equity	USA	TOP3000	Fast Expression	21	1	0.1	Market	On	Off	Verify

----------------------------------------------

rank((pretax_income - ebit)/sqrt(equity))*fam_earn_growth_rank

Equity	USA	TOP1000	Fast Expression	10	1	0.08	Industry	On	Off	Verify

----------------------------------------------

avg_news = vec_avg(nws12_afterhsz_sl);
rank(ts_sum(avg_news, 60)) > 0.5 ? 1 : rank(-ts_delta(close, 2))

Equity	USA	TOP3000	Fast Expression	4	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

rank(ts_rank(ebit/sharesout /close, 40))
Equity	USA	TOP3000	Fast Expression	4	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

change_day = (vwap - close) / close;
ts_decay_exp_window(rank(change_day), 4)

Equity	USA	TOP3000	Fast Expression	10	1	0.08	Market	On	Off	Verify

----------------------------------------------

decay_days = 2;
rel_days_since_max = rank(ts_arg_max(close, 30));
decline_pct = (vwap - close) / close;
decline_pct / min( ts_decay_linear(rel_days_since_max, decay_days), 0.20)

Equity	USA	TOP3000	Fast Expression	10	1	0.08	Market	On	Off	Verify

----------------------------------------------

buzz = ts_backfill(-vec_sum(scl12_alltype_buzzvec), 20);
ts_av_diff(buzz, 60)

Instrument Type	Region	Universe	Language	Decay	Delay	Truncation	Neutralization	Pasteurization	NaN Handling	Unit Handling
Equity	USA	TOP3000	Fast Expression	3	1	0.08	Market	On	Off	Verify

----------------------------------------------

ts_av_diff(mdf_eg3, 600)*ts_corr(mdf_eg3, mdf_sg3, 600)

Equity	USA	TOP200	Fast Expression	4	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------

trade_when(ts_mean(close,4)>=ts_mean(close,11),rank(log(fn_antidilutive_securities_excl_from_eps_a)),-1)

Equity	USA	TOP1000	Fast Expression	4	1	0.08	Subindustry	On	Off	Verify

----------------------------------------------
