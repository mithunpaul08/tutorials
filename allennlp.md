[Allennlp](https://github.com/allenai/allennlp) is no different when it comes to writing complex documentation which a common man takes hours to understand. Here are some points which took me a long time to figure out. Just in case it helps someone.

## Quick steps to get the POS tagger to run with allennlp

### if you don't want to go through their tutorial but really want to see something run:
```
mkdir allenlp
cd allennlp
git clone https://github.com/allenai/allennlp/tree/master/tutorials/tagger . (don’t forget the dot)
allennlp train tutorials/getting_started/walk_through_allennlp/simple_tagger.json --serialization-dir /tmp/tutorials/getting_started
```

Some things you need to know before reading their beginner [tutorial](https://allennlp.org/tutorials)

- Note that in the [initial tutorial](https://allennlp.org/tutorials) what they are doing is create a wrapper on the MODEL class for [simple_tagger](https://github.com/allenai/allennlp/blob/master/allennlp/models/simple_tagger.py)



Basic links/commands to install allnenlp are here
The very first get your hands dirty tutorial is here. Note that this is showing you how to write a model from scratch. Which in this case is an LSTM bAsed pos tagger whose actual code is here
I’d personally suggest don’t waste time on it, if you are trying to run an existing model. Instead jumpt to level 2
All the files you will need (including the data files and config files ) for the POS tagger project is kept here

