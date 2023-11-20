# SIA-BOT


After being involved in the stock market/ crypto market. I observed that Elon musk tweets had an real impact on price movement of Tesla.

The goal of this bot is to analyse elon musk tweets by using the Sentiment Intensity Analyser from vader. The function used, sum the number of word that are considered positive together and print a score.

I used this score to get a positive or negative signal after the tweets.

Then I will use those output to either buy or sell tesla depending on what the sentiment of the tweet is.

The Trading logic then follow, we iterate through those tweets to scan whether we have a positive of negative signal.

for i in range(len(tesla_tweets)):
    tweet_sentiment = tesla_tweets.iloc[i]['Sentiment']
    if tweet_sentiment == "Positive":
        if current_position == "None" and cash_balance > 0:
            # Achat de Tesla
            position_size = 0.2 * cash_balance  # Exemple : investir 20% du solde en TSLA
            cash_balance -= position_size # Cela soustrait le montant de la position achetée (position_size) du solde de trésorerie actuel
            portfolio["TSLA"] = position_size # Cela ajoute la position achetée dans le dictionnaire portfolio en utilisant le symbole de l'action "TSLA" comme clé et la taille de la position (position_size) comme valeur. 
            current_position = "Long"
            print("Achat de Tesla")

The parameters can be adusjted for your needs.

The Bottom of the code show how to use it with the platform Quanconnect.

PS : This bot only analyse data from 2012-2017, and is only viable for backtesting.
