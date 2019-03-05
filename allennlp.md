Basic links/commands to install allnenlp are here
The very first get your hands dirty tutorial is here. Note that this is showing you how to write a model from scratch. Which in this case is an LSTM bAsed pos tagger whose actual code is here
I’d personally suggest don’t waste time on it, if you are trying to run an existing model. Instead jumpt to level 2
All the files you will need (including the data files and config files ) for the POS tagger project is kept here
Quick steps to get the POS tagger to run with allennlp
```
mkdir allenlp
cd allennlp
git clone https://github.com/allenai/allennlp/tree/master/tutorials/tagger . (don’t forget the dot)
allennlp train tutorials/getting_started/walk_through_allennlp/simple_tagger.json --serialization-dir /tmp/tutorials/getting_started
```
