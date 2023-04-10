# Building an English-to-French Translator from Scratch with Pytorch

### This is a project meant to reinforce my personal knowledge of PyTorch, as well as explore the ins-and-outs of machine translation in general. Projects like this normally shouldn't be undertaken in a single Jupyter notebook, but it's a good way to see the whole process.

## Methods

### I used data that I found on Kaggle. This included a data set with excellent translations that was very short (<200000 entries) and a data set of somewhat poor quality that was quite large (>22 million). In order to create a large balanced data set, I used the entire 'good' data set and a sample of the 'poor' data to create a dataframe of about 300000 samples.

Data Sources:
Link: [Excellent Data but Small](https://www.kaggle.com/datasets/devicharith/language-translation-englishfrench)
Link: [Poor Quality Data but Huge](https://www.kaggle.com/datasets/dhruvildave/en-fr-translation-dataset)

### I trained the model on Google Colab GPUs and it took about two hours.

## Tokenization

### Initially, I experimented with word-based tokenization, but this resulted in a much larger model, and the inability to account for unknown words. As such I decided to implement byte-pair tokenization with the SentencePiece library. This means that case and punctuation are preserved, while also speeding up the model training. However, this makes it more difficult for the model to map word-to-word relationships. Both strategies have their strengths and weaknesses.

## Model

### I used PyTorch to make an encoder-decoder model with multi-headed attention. Obviously, this would be much easier to implement in HuggingFace, with a pretrained model. But I was interested in doing an implementation from scratch.

## Results

### Here are some of my interactions with the model after it was trained:

```
English: Hello, how are you today?
Eh bien aujourd'hui, comment êtes-vous ?

English: Excellent! The translation model seems to work!
Le modèle semble traduite !

English: Clearly, it's far from perfect.
Il est loin parfaitement loin d'être parfait.

English: But it sort of works I think.
Mais je pense que ça fonctionne.

English: And that's pretty good for only three hundred thousand data points.
Et trois points de pourcentage, les données de l'ordre de trois mille points de vente.

English: Let's try it with simpler sentences.
Essayons de simplifier les phrases.

English: I am a robot.
Je suis un robot.

English: I am from Japan.
Je viens du Japon.

English: I dance every day.
Je danse tous les jours.

English: And I like to eat pasta.
Et j'aime manger des pâtes.

English: As a basic translator, it's quite effective.
En tant que c'est un traducteur de base efficace.

English: Let's try it with more complex sentences.
Essayons de plus complexes avec ça.

English: Here's a sentence from the magazine The Economist.
Voici une phrase de magazine.

English: Ever since it was founded in 1944, the imf has had to get used to reinventing itself. Today, however, it faces an identity crisis like none before.
Aujourd'hui, il n'a pas eu de crise de crise en 1944, mais il n'a pas eu d'impression d'être l'impression

English: Well, it doesn't really work great.
Eh bien, ça ne fonctionne pas vraiment.

English: But, it's pretty good considering the limitations of the data set.
Mais il est plutôt bon de déterminer les limites des données.

English: Anyway, have a nice day, my love.
N'importe quel jour, mon amour a une belle journée.

English: Goodbye!
Bonne au revoir !
```

## Conclusion

### Obviously, these translations are far from perfect. But considering we implemented this model from scratch, it's actually pretty effective. If we had more data and several GPUs, we could definitely make a much better production-grade model.

# Stay tuned for more misadventures in machine translation!
