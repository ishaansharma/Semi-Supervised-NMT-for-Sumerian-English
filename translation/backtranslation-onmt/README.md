# Back Translation for Sumerian-English NMT

## Files
- ```backtranslateONMT.py```: To translate all Sumerian Text in a given shard using weights from the previous iteration
- ```stack.py```: To stack the backtranslated sentences to the parallel corpora for training
- ```runTransformerSumEn.sh```: To retrain the transformer model using the updated parallel data from the last step

## Running

### Back Translating, Stacking, Re-Training and then Evaluating (shard by shard)-

```
sh btPipeline.sh <weightsDir, path to directory where weights are stored> \
                 <shardSrcDir, path to directory containing the shard> \
                 <shardBackDir, directory where the backtranslated shards need to be kept> \
                 <evalSrcDir, path to directory containing the evaluation file> \
                 <evalTgtDir, directory to store the predicted translations> \
```

#### Default arguments:

- ```numShards```=9 (~85k monlingual sentences in each)
- ```weightsDir=../../weights/BT```
- ```shardSrcDir=./src```
- ```shardBackDir=./backT```
- ```evalSrcDir=../../dataset/dataToUse/UrIIICompSents```
- ```evalTgtDir=./```

## Translating (optional)

```
onmt_translate -model <path to the saved the model> -src <path to the data to be translated> -output <path to the output text file> -replace_unk -verbose
```