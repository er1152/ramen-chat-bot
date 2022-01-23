# ラーメンチャットボット
## 概要
Telegramで、いくつかの質問に答え、おすすめのラーメン屋をレコメンドするチャットボット   
## 使用データ
食べログ（https://tabelog.com/）  
• 東京都内のラーメン屋の情報（500店）  
• ラーメン屋についている口コミ（各店20件）  

## 実行環境　　
・docker環境：https://github.com/er1152/mecab-base-notebook  
・Mecab ＋ mecab-ipadic-neologd   
・Ubuntu 20.04  
・python3  
・Telegram  

・pythonモジュール  
	pandas  
	numpy  
	mecab-python3  
	gensim  
	python-telegram-bot==12.0.0  

## ロジック
・Mecab：取得した口コミからコーパスを作成  
・word2vec： 作成したコーパスを用いてモデルを構築  
・k-means：モデルをクラスタリングし、ラーメン以外の情報を除外  
・TF-IDF：↑で絞ったワードのうち店ごとにTF-IDFが高い上位20単語を抽出  
・チャットボット：ユーザからの返答をMecabで分かち書きし，word2vecのモデ
ルに含まれる単語のみを抽出し、理想のラーメン屋の情報を作成。実在するラーメン屋との類似度の高い店を勧める


## ファイルの説明
chatbot.py：メインのプログラム  
extract_words.py：形態素解析をするプログラム  
recommend.py：レコメンド部分のプログラム  
telegram_token.py：TelegramのToken  

/data  
	df_ramen_texts_tfidf_sorted_top20：.
		店の関連単語上位20個などが入ったpickleデータ  
		実行に関係します  
	word2vec.txt：
		ベクトル化可能な単語のリスト.
		実行に関係します  
	ramen_review.csv：
		口コミのスクレイピングデータ.
		実行に関係しません  
	ramen_store.cs：
		ラーメン店のスクレイピングデータ.
		実行に関係します  
/model  
	word2vec_ramen_model.model：
		word2vecモデルデータ.
		実行に関係します  
		
## 改善点
・単純にモデルの精度が悪い(そこそこ重要そうな単語が除外されるなど)  
・データが少ない  
・位置情報を使ったレコメンドもしたい   

## 実行の様子
<img src="https://user-images.githubusercontent.com/84836565/150677408-0dda53f6-aafb-4332-bdc0-a1785ad0b3c0.jpg" width="600px">
<img src="https://user-images.githubusercontent.com/84836565/150677398-9ffeea03-ae8f-4864-b24b-114c56a24657.jpg" width="600px">
<img src="https://user-images.githubusercontent.com/84836565/150677405-3ecb9ea5-fcd9-4ab6-a2e2-25a453aee140.jpg" width="600px">


