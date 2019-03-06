[Allennlp](https://github.com/allenai/allennlp) is no different when it comes to writing complex documentation which a common man takes hours to understand. Here are some points which took me a long time to figure out. Just in case it helps someone.

## Qn) Don't feel like reading a tutorial, I want to see something running. How?

### Ans: Quick steps to get the POS tagger to run with allennlp (i.e if you don't want to go through their tutorial but really want to see something running):
```
mkdir allenlp
cd allennlp
git clone https://github.com/allenai/allennlp.git . (don’t forget the dot)
allennlp train tutorials/getting_started/walk_through_allennlp/simple_tagger.json --serialization-dir /tmp/tutorials/getting_started
```

## Qn) Fine. Now I want to try out running a basic model they have written in PyTorch. What all do I need to do?

### Ans: Some things you need to know before reading their beginner [tutorial](https://allennlp.org/tutorials)

- Note that in the [initial tutorial](https://allennlp.org/tutorials) what they are doing is create a wrapper on the MODEL class for [simple_tagger](https://github.com/allenai/allennlp/blob/master/allennlp/models/simple_tagger.py)
- which means you are writing a bunch of read data, create their custom classes which are needed to run this model.
- What that means is if you want to use the simple_tagger instead of the lstm_tagger they have provided in the [tutorial](https://allennlp.org/tutorials) page, all you have to do is replace the [lstm_tagger](https://github.com/allenai/allennlp/blob/master/tutorials/tagger/basic_allennlp.py#L153) with the simple tagger class given [here](https://github.com/allenai/allennlp/blob/master/allennlp/models/simple_tagger.py#L19).


## Qn) I want to run one of the off the shelf models with the data set they have provided. what to do? 
```
mkdir allenlp
cd allennlp
git clone https://github.com/allenai/allennlp.git . (don’t forget the dot)
allennlp train training_config/decomposable_attention.jsonnet -s output_path
```

### Extra info: A list of allennlp's ready to go models are kept [here](https://allennlp.org/models). Note that all you can change here is the config parameters, i.e epochs, patience etc in the config file kept [here](https://github.com/allenai/allennlp/blob/master/training_config/decomposable_attention.jsonnet). If you want to instead feed it your own data, you will write a Dataset reader yourself.

for example if you want to run decomposable attention over SNLI data, use [this](https://s3-us-west-2.amazonaws.com/allennlp/models/decomposable-attention-elmo-2018.02.19.tar.gz) model.

## Qn) Running the above says its expecting GPU, but I don't have one?

## Ans: Open the config [file](https://github.com/allenai/allennlp/blob/master/training_config/decomposable_attention.jsonnet) and change the `"cuda_device": -1`

Basic links/commands to install allnenlp are here
The very first get your hands dirty tutorial is here. Note that this is showing you how to write a model from scratch. Which in this case is an LSTM bAsed pos tagger whose actual code is here
I’d personally suggest don’t waste time on it, if you are trying to run an existing model. Instead jumpt to level 2
All the files you will need (including the data files and config files ) for the POS tagger project is kept here

