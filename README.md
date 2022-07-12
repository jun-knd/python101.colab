# Colaboratoryを利用したPython実行環境

## Colaboratory(以下Colab)の特徴

- Webブラウザ上のPython実行開発環境
- 環境構築が不要
- GPU への無料アクセス
- 追加ライブラリの組み込みが可能
- Markdownの文章とPythonコードを併記可能(Jupyter Notebook形式)  

## Colab の導入

Colabの導入は下記URLにアクセスするだけです。  
<https://colab.research.google.com/>
![image](https://user-images.githubusercontent.com/38905609/175796715-c761c3b5-4ea1-4a5c-a88d-e53d8968034b.png)

## Colabの設定

- ランタイム-ランタイムのタイプを変更からGPUを指定可能。  
![image](https://user-images.githubusercontent.com/38905609/174577446-94111208-5da7-4b03-9673-fef83d57c7ad.png)
![image](https://user-images.githubusercontent.com/38905609/174577869-26de9308-dcde-4760-9086-4c56652cfb17.png)

- ツール-設定 から環境設定可能。  
パワーレベル、コーギーモード、猫モード、カニモードを必要に応じて設定すると良いでしょう。
![image](https://user-images.githubusercontent.com/38905609/174462253-046191a2-7762-4940-9590-080c3266b2c3.png)
![image](https://user-images.githubusercontent.com/38905609/174462281-654bee21-ee70-4cdb-a5c9-48edf2fa02f9.png)

## GitHubをColabから開く

下記リンクを記載することで、`Open in Colab`のリンクを設定できます。

```html
<a href="https://colab.research.google.com/github/[github-id]/[github-path]" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

例)
<a href="https://colab.research.google.com/github/jun-knd/python101.colab/blob/main/Python101.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>
```

[![image](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jun-knd/python101.colab/blob/main/Python101.ipynb)

## Pythonコードエリアの追加

![image](https://user-images.githubusercontent.com/38905609/175796802-7be519fd-80af-4341-82e4-065fb476664f.png)

👇 追加されたコードエリアにPythonコードを記載する。
![image](https://user-images.githubusercontent.com/38905609/175796892-44657224-a8f4-4086-87af-9887be4d56ea.png)

## Python コードサンプル①

- 数値計算  
$x = a \times b$  
下記コードサンプルは単純に積を求める。

```python
x = 160 * 10000
print("掛け算")
print(x)
print("フォーマット")
print("{:,}".format(x))
```

![image](https://user-images.githubusercontent.com/38905609/175796990-c58357b4-f227-49ca-9790-0d549be811a1.png)

## Python コードサンプル②

- round関数は四捨五入ではない  
- 四捨五入は`Decimal#quantize()`を利用する  

```python
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

## Python コードサンプル③

- グラフ描画  

```python
import pandas as pd
import pandas_datareader.data as web
import datetime
import mplfinance as mpf

start = datetime.date(2021,1,1)
end = datetime.date(2022,7,14)

stock_code = "6502"

stockdata=web.DataReader(stock_code +".JP", "stooq",start,end)

df = stockdata.sort_index()
mpf.plot(df, title=stock_code, type='candle', mav=(5, 25), volume=True)
```

- モジュール依存関係でエラー発生の場合、`mplfinance`をpipを使ってインストールする。

```python
!pip install mplfinance
```

![image](https://user-images.githubusercontent.com/38905609/175797021-00bb848d-c991-4a57-b609-462d3a57330e.png)

- pip コマンドはコードエリアに先頭"!"付きで記載することで発行可能  
![image](https://user-images.githubusercontent.com/38905609/175797045-370c14cd-1037-4915-9f13-b1041ec2f30e.png)

## 👇GitHubは以下参照下さい

- <https://github.com/jun-knd/python101.colab>

