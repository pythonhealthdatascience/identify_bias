# Identifying bias

Trying out tools for identifying bias.

## `Dbias`

> Raza, S., Reji, D.J. & Ding, C. Dbias: detecting biases and ensuring fairness in news articles. Int J Data Sci Anal 17, 39–59 (2024). https://doi.org/10.1007/s41060-022-00359-4

**Availability:** The Python code is not available, but `.whl` and `.tar.gz` files are provided on [GitHub](https://github.com/dreji18/Fairness-in-AI), and the package can be installed from [PyPI](https://pypi.org/project/Dbias/). The repository is licensed under MIT.

**Installation:** We based our environment on their `requirements.txt`, and note that just trying to pip install the package into an empty environment will fail (as the package requires Python 3.6-8, but package managers will install a recent version of the `spacy` dependency which requires Python 3.9+).

```
conda env create --file dbias/environment.yaml
conda activate bias_dbias
```

**Usage:** Only the `bias_classification` module successfully imports - the others have an error:

```
---------------------------------------------------------------------------
OSError                                   Traceback (most recent call last)
Cell In[1], line 1
----> 1 from Dbias.text_debiasing import * 
      3 # returns unbiased recommendations for a given sentence fragment.
      4 run("Billie Eilish issues apology for mouthing an anti-Asian derogatory term in a resurfaced video.", show_plot = True)

File ~/mambaforge/envs/bias/lib/python3.8/site-packages/Dbias/text_debiasing.py:34
     30 classifier = pipeline('text-classification', model=model, tokenizer=tokenizer) # cuda = 0,1 based on gpu availability
     32 # ner model
     33 #pip install https://huggingface.co/d4data/en_pipeline/resolve/main/en_pipeline-any-py3-none-any.whl
---> 34 nlp = spacy.load("en_pipeline")
     36 # masked language model
     37 tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")

File ~/mambaforge/envs/bias/lib/python3.8/site-packages/spacy/__init__.py:51, in load(name, vocab, disable, exclude, config)
     30 def load(
     31     name: Union[str, Path],
     32     *,
   (...)
     36     config: Union[Dict[str, Any], Config] = util.SimpleFrozenDict(),
     37 ) -> Language:
     38     """Load a spaCy model from an installed package or a local path.
     39 
     40     name (str): Package name or model path.
   (...)
     49     RETURNS (Language): The loaded nlp object.
     50     """
---> 51     return util.load_model(
     52         name, vocab=vocab, disable=disable, exclude=exclude, config=config
     53     )

File ~/mambaforge/envs/bias/lib/python3.8/site-packages/spacy/util.py:427, in load_model(name, vocab, disable, exclude, config)
    425 if name in OLD_MODEL_SHORTCUTS:
    426     raise IOError(Errors.E941.format(name=name, full=OLD_MODEL_SHORTCUTS[name]))  # type: ignore[index]
--> 427 raise IOError(Errors.E050.format(name=name))

OSError: [E050] Can't find model 'en_pipeline'. It doesn't seem to be a Python package or a valid path to a data directory.
```