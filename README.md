# 概要
Telegramで、いくつかの質問に答え、おすすめのラーメン屋をレコメンドするチャットボット   
## 使用データ
食べログ（https://tabelog.com/）  
• 東京都内のラーメン屋の情報（500店）  
• ラーメン屋についている口コミ（各店20件）  

# 実行環境　　
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

# ファイルの説明
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


