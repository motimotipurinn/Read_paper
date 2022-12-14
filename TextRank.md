TextRankはGoogleの開発したPageRankというアルゴリズムを自然言語に拡張したものである。
PageRankは各頂点が関連のある頂点に対し投票を行い、投票を多くされた点はより重要度が上がり、投票をしたほうも重要度が上がるというものである
式で表すと
```math
S(V_i)=(1-d)+d*\sum_{j∈In(V_i)} \frac{S(V_j)}{Out(V_j)}
```
であり、dを減衰定数とする。これを任意の点からスタートして収束するまで回して、$S(V_i)$でソートすることで文章の重要度が得られる。
TextRankでは自然言語について扱うために文や単語同士の繋がりが重要となるため、さっきの式に重みを乗せたものが考えられる
```math
WS(V_i)=(1-d)+d*\sum_{j∈In(V_i)} \frac{w_{ij} \ WS(V_j)}{\sum_{k∈Out(V_j)}w_{jk}}
```
となる。単語抽出では、形態素解析をしたあと構文チェックを通った単語が単語同士の出現位置の距離によって制御される共起関係によって重みをつけている。
また文章抽出では各文章の共通要素によって文章同士の重み付けをすることができる

https://aclanthology.org/W04-3252/
