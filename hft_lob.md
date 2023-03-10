一、Order aggressiveness
（1）订单侵略性，其实就是挂单的激进程度。假设你是买家，你挂单的价格越高，你就越激进；反过来，你是卖家，你挂单价格越低，你越是激进的卖家。举个例子，买家挂单越接近bid1，越激进；卖家挂单越接近ask1，越激进；

（2）订单侵略性，体现了买家/卖家完成交易的迫切程度。通过整个订单薄，我们可以知道所有买家整体的激进程度、和所有卖家整体的激进程度；通过这个，就能构建一系列因子了。此外，买卖aggressiveness的差异，也是一系列因子；

（3）一个订单的执行概率和订单薄的厚度、参与者对即将到来的订单的预期有关；买盘越厚，一个潜在的买家下market order的概率更大；这套说法对卖方同样适用；bid ask的厚度体现了看涨和看跌者的相对力量。

（4）不要用静态的思维来看待订单薄，要从动态的角度来分析。订单薄性质的变化，体现了多空力量的动态变化，是未来价格走势的重要体现；在这个问题上，时间序列的建模是很有必要的。



二、order book shape
（1）order book shape，就是订单薄所呈现的形状。

（2）很多学术研究表明，股票的order book的平均形态就是Humped，就是整个订单薄上有一块隆起的地方；

（3）个股来说，我觉得，离不开几种情况。第一，就是Humped，只是这个顶点不同，而且可能随着时间的变化而变化；第二，可能是双峰的、甚至是多峰的Humped；第三，可能是没有峰，就是矩形分布；第四，可能就在某些档位有分布；第五，可能是单调的，比如从第一档往后几乎单调上升或者下降，单调的函数可以是线性的，也可以是concave或者convex；

（4）上面，是从全局的角度来描述LOB（limit order book简称，下同) 状态的一种方法。也可以只关注一些特殊的点，比如，在某个偏离bid/ask的位置有个奇怪的大单；然后，还要加入时间维度。前面两个，都是静态的、截面的。

（5）humped位置：很多实证研究，都表明，LOB的平均形态，就是humped，只是这个humped的位置不同，这个顶点的位置，可以作为一个因子。比如，买单的顶点位置，是位于0-10%、10-20%等的哪个位置；此外，还需要关注这个hump位置随时间的迁移。

（6）order book slope：订单薄斜率，描述订单薄上的价格和该价格处的挂单量之间的关系。这个slope属于shape的分支，其含义和aggressiveness类似；



三、撤单
（1）撤单行为，不仅反映了交易者的观点的变化，还会影响其他交易者；根据买卖双方各自的撤单量、撤单金额、撤单价位、大单超大单的撤单情况，可以构建很多因子；

（2）和订单薄不同，撤单类因子，是一个流量变量，它需要考虑一个时间段的因子；构建撤单因子时，一定不要独立地看待某段时间的撤单行为，而需要结合实际的成交情况，这才是这段时间内多空双方博弈的信息全集（相对的）；

（3）fleeting order：即挂单后短时间内又撤掉的订单；除了正常交易情况下撤单去追跑掉的价格外，fleeting order还有欺骗对手的作用，挂单者想制造假象，以诱导其他投资者（spoofing order）；比如，前面降了order book shape，如果你采用了这种因子进行交易，那么你的对手以通过fleeting order来扰乱order book，从而让你的系统发出虚假的信号；



四、事件聚集
（1）定义一些事件，比如撤单、挂买一单、超大买卖单出现，然后在一段时间内统计事件发生的频率，可以构建很多个系列的因子；这是高频数据低频化的常见思路；

（2）一些事件具有聚集的特性，原因有：交易者拆分大单来掩盖交易意图；交易者之间的模仿；不同交易者对新闻的反应（反应是一致的，只是有先有后）；为了在竞价上击败其他交易者；



五、订单薄韧性
（1）如果来了个大的市价卖单，然后，当然，买单被吃掉很多；但是通常会回复一部分。比如，有个100手的市价卖单，刚好吃掉了所有报价21元以上的单；后来，21元以上的买单恢复了80手。那么，这个回复能力，就是80%。

（2）订单薄韧性，反映了一部分股票的属性。是个很有意思的因子。



六、异常挂单
（1）有时候，在原理买一和卖一的地方（比如涨停价跌停价，会存在大量挂单。正常情况下，这些订单几乎不可能成交。

（2）类似这样的异常挂单，十分重要。依据这些数据来构建的因子，很有信息量。



七、逐笔数据：主动买卖
（1）判断一笔交易属于主动买还是主动卖，通常以一笔交易的买卖双方的订单到底先后顺序来定；

（2）在实际中，逐笔交易买卖单判断十分重要；像我们常见的资金流这类指标，就是这么计算的；

（3）逐笔数据可以构建的因子很多，主动买卖算一类；

（4） 举例：日内累计主买率、日内累计资金净流入、日内累计大单资金流入率、日内累计小单资金流入率，等等；