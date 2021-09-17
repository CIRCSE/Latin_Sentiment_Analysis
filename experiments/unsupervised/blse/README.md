# Bilingual Sentiment Embeddings

Codice originale [https://github.com/jerbarnes/blse](https://github.com/jerbarnes/blse)

Paper [https://aclanthology.org/P18-1231.pdf](https://aclanthology.org/P18-1231.pdf)

## Scelta training nella lingua target (inglese)

Il sistema BLSE usa di default il datased OpeNER che, benché sia annotato a livello di frasi, oltre a non avere la classe neutra, è formato da recensioni di hotel quindi il sentiment è quello dell'opinione verso l'hotel. Potrebbe essere meglio usare un dataset creato per l'emotion analysis in modo che sia più simile alla nostra annotazione?

Possibili dataset alternativi sono elencati qua sotto: nessuno annota a livello di frase.

1. SemEval-2018 Task 1: Affect in Tweets (AIT-2018) [https://competitions.codalab.org/competitions/17751#learn_the_details-overview](https://competitions.codalab.org/competitions/17751#learn_the_details-overview): già diviso in train, dev, test set. In particolare possono essere usati i dati di uno dei due task sotto descritti:
    * V-oc (a sentiment analysis, ordinal classification, task): Given a tweet, classify it into one of seven ordinal classes, corresponding to various levels of positive and negative sentiment intensity, that best represents the mental state of the tweeter. 2,567 tweet.
--> La classe 0: neutral or mixed mental state can be inferred. Neutro e mixed sono uniti nella stessa classe.
    * E-c (an emotion classification task): Given a tweet, classify it as 'neutral or no emotion' or as one, or more, of eleven given emotions that best represent the mental state of the tweeter. 10,983 tweet.
--> posso passare dalle emozioni specifiche alle nostre classi. 
positive: joy, love, optimism, trust
negative: anger, pessimist, disgust, fear, sadness
ambigue (da eliminare): anticipation, surprise

2. DENS dataset [https://aclanthology.org/D19-1656.pdf](https://aclanthology.org/D19-1656.pdf): data contains 9710 passages extracted from online narratives on wattpad and literature on project Gutenberg and classified into joy, sadness, anger, fear, anticipation, surprise, love, disgust, neutral.
--> posso passare dalle emozioni specifiche alle nostre classi.

3. GoEmotions [https://github.com/google-research/google-research/tree/master/goemotions](https://github.com/google-research/google-research/tree/master/goemotions): corpus of 58k carefully curated comments extracted from Reddit, with human annotations to 27 emotion categories or Neutral.
--> posso passare dalle emozioni specifiche alle nostre classi.

4. PO-EMO [https://github.com/tnhaider/poetry-emotion/tree/master/tsv](https://github.com/tnhaider/poetry-emotion/tree/master/tsv): i dati inglesi ammontano a circa 1300 versi annotati, manca neutrale e mixed
--> molto piccolo

5. Poem-Sentiment [https://github.com/google-research-datasets/poem-sentiment](https://github.com/google-research-datasets/poem-sentiment): 892 versi annotati con 4 classi come le nostre
--> molto piccolo

## Bilingual lexicon
Traduzione dei lemmi con polarità positiva (1 e 0.5) e negativa (-1 -0.5) usando Lewis & Short. Per lemmi senza traduzione ho lavorato a mano usando Logeion. Non sono inseriti lemmi con polarità neutra e quelli che richiedono una traduzione con espressione multi-parola. La lista finale  (*en-lat.txt*) comprende 3.000 lemmi.

## Embeddings
Per il latino userò i nostri embeddings [https://embeddings.lila-erc.eu/samples/download/](https://embeddings.lila-erc.eu/samples/download/).
Per l'inglese la maggior parte degli embeddings in circolazione sono basati sulle forme. I seguenti sono addestrati su testi lemmatizzati automaticamente:
- [http://vectors.nlpl.eu/explore/embeddings/en/models/](http://vectors.nlpl.eu/explore/embeddings/en/models/): però hanno anche l'informazione del POS (lemma_POS).
- [https://embeddings.sketchengine.eu/static/index.html](https://embeddings.sketchengine.eu/static/index.html): anche con lemmi in lowercase. Oltre a embeddings addestrati sull'Early English, ce ne è uno addestrato sul web (20 billion token) e uno sul British National Corpus (10 million tokens). 
- [http://vectors.nlpl.eu/repository/](http://vectors.nlpl.eu/repository/) repository con svariati embeddings per molte lingue, varie dimensioni anche lemmatizzati