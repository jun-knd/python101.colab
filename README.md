# Colaboratoryを利用したPython実行環境

## Colaboratory(以下Colab)の導入
https://colab.research.google.com/

## Colabの特徴
  - Webブラウザ上の開発環境
  - 環境構築が不要
  - GPU への無料アクセス

## Colabの設定
ランタイム-ランタイムのタイプを変更からGPUを指定可能。  

![image](https://user-images.githubusercontent.com/38905609/174577446-94111208-5da7-4b03-9673-fef83d57c7ad.png)
![image](https://user-images.githubusercontent.com/38905609/174577869-26de9308-dcde-4760-9086-4c56652cfb17.png)



ツール-設定 から環境設定可能。  
パワーレベル、コーギーモード、猫モード、カニモードを必要に応じて設定すると良いでしょう。
![image](https://user-images.githubusercontent.com/38905609/174462253-046191a2-7762-4940-9590-080c3266b2c3.png)
![image](https://user-images.githubusercontent.com/38905609/174462281-654bee21-ee70-4cdb-a5c9-48edf2fa02f9.png)



## GitHubをColabから開く
下記リンクを記載することで、`Open in Colab`のリンクを設定できます。
```
<a href="https://colab.research.google.com/github/[github-id]/[github-path]" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

例)
<a href="https://colab.research.google.com/github/jun-knd/python101.colab/blob/main/Python101.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>
```
<a href="https://colab.research.google.com/github/jun-knd/python101.colab/blob/main/Python101.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>


# Python コードサンプル①
## 数値計算
$x = a \times b$

下記コードサンプルは単純に積を求める。
```
x = 160 * 10000
print("掛け算")
print(x)
print("フォーマット")
print("{:,}".format(x))
```


# Python コードサンプル②
## round関数は四捨五入ではない
## 四捨五入は`Decimal#quantize()`を利用する
```
from decimal import Decimal, ROUND_HALF_UP, ROUND_HALF_EVEN

target = 2.5

print("target = 2.5")
print("round(target)👇")
print(round(target))

print("あれ?")

print("Decimal(str(target)).quantize(Decimal('0'), rounding=ROUND_HALF_UP)👇")
print(Decimal(str(target)).quantize(Decimal('0'), rounding=ROUND_HALF_UP))
print("そうそう！")
```

# Python コードサンプル③
## グラフ描画
```
# コード領域
import pandas as pd
import pandas_datareader.data as web
import datetime
import mplfinance as mpf

start = datetime.date(2021,1,1)
end = datetime.date(2022,6,17)

stock_code = "6502"

stockdata=web.DataReader(stock_code +".JP", "stooq",start,end)

df = stockdata.sort_index()
mpf.plot(df, title=stock_code, type='candle', mav=(5, 25), volume=True)
```

モジュール依存関係でエラー発生の場合、`mplfinance`をpipを使ってインストールする。

```
!pip install mplfinance
```

## 👇GitHubは以下参照下さい。
https://github.com/jun-knd/python101.colab
