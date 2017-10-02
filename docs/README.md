# IE Visual Library in Stata

## [Bar plots](https://github.com/worldbank/Stata-IE-Visual-Library/tree/master/Library/Bar%20plots)

### [Bar plot of two variables by treatment](https://github.com/worldbank/Stata-IE-Visual-Library/tree/master/Library/Bar%20plots/Bar%20plot%20of%20two%20variables%20by%20treatment)

![plot](https://user-images.githubusercontent.com/15252541/30933373-67fafece-a398-11e7-84f3-c2294cd9f3de.png)

```stata
# d;
graph bar w_total_val_harvested_a w_total_val_inputs_a, 
	  over(treated)		
	  bargap(-30)
	  legend(label(1 "Total Value Harvested")
			 label(2 "Total Value Inputs"))
	  bar (1, color("0 102 102") ) 
	  bar (2, color("153  0 76") ) 
	  ytitle ("Value in RWF")	
	  title  ("Harvested value and Input Value")
	  subtitle ("By treatment")
	  note ("Note: Variables are winsorized at 0.01");
# d cr
```


## [Density plots](https://github.com/worldbank/Stata-IE-Visual-Library/tree/master/Library/Density%20plots)

### [Density plot with averages](https://github.com/worldbank/Stata-IE-Visual-Library/tree/master/Library/Density%20plots/Density%20plot%20with%20averages)

![plot](https://user-images.githubusercontent.com/15252541/30933363-622abee4-a398-11e7-98a6-432337ed7375.png)

```stata
twoway 	(kdensity revenue if post == 0, color(gs10)) ///
	(kdensity revenue if post == 1, color(emerald)), ///
	xline(`pre_mean', lcolor(gs12) lpattern(dash)) ///
	xline(`post_mean', lcolor(eltgreen) lpattern(dash)) ///
	legend(order(1 "Pre-treatment" 2 "Post-treatment")) ///
	xtitle(Agriculture revenue (BRL thousands)) ///
	ytitle(Density) ///
	bgcolor (white) graphregion(color(white))
			
```
###### Contribution: `@luizaandrade`


## [RD plots](https://github.com/worldbank/Stata-IE-Visual-Library/tree/master/Library/RD%20plots)
### [Regression discontinuity plot with confidence intervals](https://github.com/worldbank/Stata-IE-Visual-Library/tree/master/Library/RD%20plots/Regression%20discontinuity%20plots%20with%20confidence%20intervals)

![rdplot1](https://user-images.githubusercontent.com/15252541/30933351-576483a0-a398-11e7-84d1-0b143f353578.png)

```stata
twoway  (lpolyci tmt_status pmt_score if pmt_score < `cutoff', clcolor(navy) acolor(gs14)) ///
	(lpolyci tmt_status pmt_score if pmt_score > `cutoff', clcolor(navy) acolor(gs14)), ///
	xline(`cutoff', lcolor(red) lwidth(vthin) lpattern(dash)) ///
	ytitle(Probability of receiving treatment) ///
	xtitle(Proxy means test score) ///
	legend(off) ///
	bgcolor (white) graphregion(color(white))  ///
	note("Note: gray area is 95% confidence interval.")
```
###### Contribution: `@luizaandrade`


## [Scatter plots](https://github.com/worldbank/Stata-IE-Visual-Library/tree/master/Library/Scatter%20plots)

### [Scatter plot with fitted line](https://github.com/worldbank/Stata-IE-Visual-Library/tree/master/Library/Scatter%20plots/Scatter%20plot%20with%20fitted%20line)

![scatterplot1](https://user-images.githubusercontent.com/15252541/30933356-5dcac8d0-a398-11e7-8dc9-b32d3cdc55f3.png)

```stata
twoway 	(scatter revenue area_cult if post == 0, msize(vsmall) mcolor(gs14)) ///
	(lfit revenue area_cult if post == 0, color(gs12)) ///
	(scatter revenue area_cult if post == 1, msize(vsmall) mcolor(stone)) ///
	(lfit revenue area_cult if post == 1, color(sand)), ///
	ytitle(Agriculture revenue (BRL thousands)) ///
	xtitle(Cultivated area) ///
	legend(order(2 "Pre-treatment" 4 "Post-treatment")) ///
	bgcolor (white) graphregion(color(white))
```
###### Contribution: `@luizaandrade`

### [Scatter plot with fitted line and confidence interval]()

![scatterplot2](https://user-images.githubusercontent.com/15252541/31103991-270f0464-a7a8-11e7-83a0-7edd4420c052.png)

```stata
twoway ///
(lfitci jobs_scarce_code avg_growth ) ///
(scatter jobs_scarce_code avg_growth if continent == "Africa", mcolor(cranberry) m(O) )  ///
(scatter jobs_scarce_code avg_growth if continent == "Asia",   mcolor(dkgreen) m(D) ) ///
(scatter jobs_scarce_code avg_growth if continent == "Europe", mcolor(ebblue ) m(T) ) ///
(scatter jobs_scarce_code avg_growth if continent == "North America", mcolor(dkorange) m(O)) ///
(scatter jobs_scarce_code avg_growth if continent == "Oceania", mcolor(navy) m(D) ) ///
(scatter jobs_scarce_code avg_growth if continent == "South America", mcolor(red) m(T)),  ///
xlabel(-5(5)15) 		///
xtitle("Average Annual GDP per Capita Growth Rate (%)", axis(1)) ///
ylabel(0(0.2)1) ///
ytitle("Gender Value Indicator" ) ///
legend(order( 3 4 5 6 7 8) label(3 "Africa") label(4 "Asia")  label(5 "Europe") ///
label(6 "North America") label(7 "Oceania") label(8 "South America")    ///
ring(0) position(4)) ///
title("Gender Value Indicator and GDP per Capita Growth" "Correlation")  ///
note("Source: World Values Survey (2014 or last available year) and World Bank") /// 
graphregion(color(white)) bgcolor(white)
```
###### Contribution: `@marcelamello90`


