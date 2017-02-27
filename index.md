## Mortgage Plot
![original resid dist](https://github.com/xinyix/Mortgage/blob/master/interest_principal.png?raw=true)

```
M <- 300    300 months
payment <- 7718.1622	 ## monthly payment
r <- 0.08/12    ## monthly interest

## declare vectors
interest <- rep(0, M)
principal <- rep(0, M)
capital <- rep(0, M)
idx <- rep(0, M)

## initialize
capital[1] <- 1000000
interest[1] <- capital[1] * r
principal[1] <- payment - interest[1]
idx[1] <- 1

for (i in 2:M) {
	capital[i] <- capital[i-1] - principal[i-1]
	interest[i] <- capital[i] * r
	principal[i] <- payment - interest[i]
	idx[i] <- i
}

## plot 
plot(idx, interest, xlab="month", ylab="amount", main="Principal and Interest Amounts as a function of Payment", type="b", pch=17, col="red")
lines(idx, principal, type="b", pch=13, lty=2, col="blue")
legend("topright", legend=c("Interest", "Principal"), col=c("red", "blue"), lty=1:2, cex=1)
```
