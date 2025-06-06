# 下单模式详解

<figure><img src="../../../.gitbook/assets/Group 47302.png" alt="" width="563"><figcaption></figcaption></figure>

## 限价下单

限价下单模式下，程序将按照交易所币对当前最新标记价格进行委托开仓，直到订单按委托价格成交。

在该模式下订单不一定能在短时间内100%成交，尤其在行情急速拉升或下跌的过程中（当价格迅速偏离委托价格时，订单可能不会立马完全成交[^1]）[^2]。[^3]

## 市价下单

市价下单模式下，程序将不断按对手价格开仓，确保订单以最快速度100%成交。[^4]



> 用户做多时，程序将不断按照最新的卖一价开多；即，在上涨行情中，如果订单没有100%完成开多时，Bitrader会自动撤单未成交订单，重新按照最新的卖一价（由于行情上涨，此时的卖一价比原来的价格高）下单开多，直到订单全部成交为止。

> 用户做空时，程序将不断按照买一价开空；即，在下跌行情中，订单没有100%完成开空时，Bitrader会自动撤单未成交订单，重新按照最新的买一价（由于行情下跌，此时的买一价比原来的价格更低）下单开空，直到订单全部成交为止。

在该模式下，订单的成交成本将比限价下单模式高。

## 计划委托

计划委托模式下，程序将按用户预先设定的“开仓价、平仓价”在条件达成时执行开仓、平仓委托。

{% hint style="info" %}
开仓价：程序根据用户设定的开仓“上浮”或“下浮”百分比自动计算而出，它表示以比现在便宜a%的价格进行委托。

平仓价：程序根据用户设定的平仓“上浮”或“下浮”百分比自动计算而出，它表示在平仓时期望获得的b%的利润空间。
{% endhint %}

> 用户做多时，程序将按用户设定值（比行情价低a%的价格）委托开仓，当价格下跌至设定值价位时开仓订单即可成交；开仓成功后，程序将自动按照设定的“盈利期望（比开仓价高b%的价格）”委托平仓，当价格上涨至平仓价格时，订单即可自动成交。

> 用户做空时，程序将按用户设定值（比行情价高a%的价格）委托开仓，当价格上涨至设定值价位时开仓订单即可成交；开仓成功后，程序将自动按照设定的“盈利期望（比开仓价低b%的价格）”委托平仓，当价格下跌至平仓价格时，订单即可自动成交。

在该模式下，订单的成交成本将比现价下单模式低。



[^1]: 以价格优先

[^2]: 以价格优先

[^3]: 以价格优先

[^4]: 以成交优先
