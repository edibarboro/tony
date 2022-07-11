study(title="Tony's EMA Scalper - Buy / Sell", shorttitle="TUX EMA Scalper", overlay=true)
len = input(20, minval=1, title="Length")
src = input(close, title="Source")
out = ema(src, len)
plot(out, title="EMA", color=blue)
last8h = highest(close, 8)
lastl8 = lowest(close, 8)

plot(last8h, color=red, linewidth=2)
plot(lastl8, color=green, linewidth=2)


bearish = cross(close,out) == 1 and close[1] > close 
bullish = cross(close,out) == 1 and close[1] < close 

plotshape(bearish, color=red, style=shape.arrowdown, text="Sell", location=location.abovebar)
plotshape(bullish, color=green, style=shape.arrowup, text="Buy", location=location.belowbar)
