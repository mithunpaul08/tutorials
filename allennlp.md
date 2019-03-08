[Allennlp](https://github.com/allenai/allennlp) is no different when it comes to writing complex documentation which a common man takes hours to understand. Plus you don't really have time to write up their basic tutorial and learn. You would rather learn on the way. If yes, here are some points which took me a long time to figure out. Just in case it helps someone. I went level by level where 

# level1-Basic:

## Qn) Don't feel like reading a tutorial, I want to see something running. How?

### Ans: Quick steps to get the POS tagger to run with allennlp (i.e if you don't want to go through their tutorial but really want to see something running):
```
mkdir allenlp
cd allennlp
git clone https://github.com/allenai/allennlp.git . (don’t forget the dot)
allennlp train tutorials/getting_started/walk_through_allennlp/simple_tagger.json --serialization-dir /tmp/tutorials/getting_started
```

## Qn) Fine. Now I want to try out running a basic model they have written in PyTorch. What all do I need to do?

### Ans: 

I'd usually suggest trying out their beginner tutorial. But here are some things you need to know before reading their beginner [tutorial](https://github.com/allenai/allennlp/tree/master/tutorials/tagger).






Extra Info:
- **Note: Whatever you do: don't even think about going through the version of the [tutorial](https://allennlp.org/tutorials) in their website. In an effort to make the same tutorial more fancy scrolling/looking they made it so damn confusing**

- Note that in the initial tutorial what they are doing is create a wrapper on the MODEL class for [simple_tagger](https://github.com/allenai/allennlp/blob/master/allennlp/models/simple_tagger.py)
- which means you are writing a bunch of read data, create their custom classes which are needed to run this model.
- What that means is if you want to use the simple_tagger instead of the lstm_tagger they have provided in the [tutorial](https://allennlp.org/tutorials) page, all you have to do is replace the [lstm_tagger](https://github.com/allenai/allennlp/blob/master/tutorials/tagger/basic_allennlp.py#L153) with the simple tagger class given [here](https://github.com/allenai/allennlp/blob/master/allennlp/models/simple_tagger.py#L19).

- don't expect all the links to work in any of the tutorial pages. They don't. Instead i'd suggest going to the [docs homepage](https://allenai.github.io/allennlp-docs/) and searching for whatever you had clicked on.

### or try this:

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

## Ans: 
Open the config [file](https://github.com/allenai/allennlp/blob/master/training_config/decomposable_attention.jsonnet) and change the `"cuda_device": -1`

## Qn) ok am ready to feed in my own data. How do I do that?

## Ans: 
Its time for 
# level2-Intermediate. 

## If you want to read their tutorial and get bored.
The first two part of the table of contents in [this](https://github.com/allenai/allennlp/tree/master/tutorials) page is what I already made you guys do. Now for the data part read [this](https://github.com/allenai/allennlp/blob/master/tutorials/getting_started/predicting_paper_venues/predicting_paper_venues_pt1.md) tutorial

**Note: be prepared to go through multiple iterations of both the basic and intermediate tutorials before you can completely understand everything. **

## or If you want to just get going.
- create a new python project
- create a file called wrapper_model.py
- copy everything from [this](https://github.com/allenai/allennlp/blob/master/tutorials/tagger/basic_allennlp.py) to wrapper_model.py
- replace the model class part (i.e from line [153](https://github.com/allenai/allennlp/blob/master/tutorials/tagger/basic_allennlp.py#L153) to line [257](https://github.com/allenai/allennlp/blob/master/tutorials/tagger/basic_allennlp.py#L227) with the class of hte model you want to use. For example [here](https://github.com/allenai/allennlp/blob/master/allennlp/models/decomposable_attention.py) is the  corresponding class for Decomposable Attention model.
- remember to copy in the missing imoprt statements too from the class file
- create another file called da.jsonnet
- copy paste everything from [this](https://github.com/allenai/allennlp/blob/master/training_config/decomposable_attention.jsonnet) file here
- replace the `train_data_path` and `validation_data_path` paths to your own data. Better you copy it over to this folder.
- from command line type
`allennlp train decomposable_attention.jsonnet --serialization-dir /tmp/da`

## FAQ

#### Qn) 
I get the error `allennlp.common.checks.ConfigurationError: "The serialization directory already exists but doesn't contain a config.json. You probably gave the wrong directory.` 
What does that mean?

#### Ans:
do `rm -rf output_path` and run the command again.


