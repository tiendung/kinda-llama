## https://huggingface.co/datasets/wikipedia

Wikipedia dataset containing cleaned articles of all languages. The datasets are built from the Wikipedia dump (https://dumps.wikimedia.org/) with one split per language. Each example contains the content of one full Wikipedia article with cleaning to strip markdown and unwanted sections (references, etc.).

The articles are parsed using the mwparserfromhell tool.

To load this dataset you need to install Apache Beam and mwparserfromhell first:

```sh
pip3 install datasets apache_beam mwparserfromhell
```

```py
from datasets import load_dataset
# e = load_dataset("wikipedia", "20220301.en")
# Downloading:  50%|████████████████████▍                   | 10.1G/20.3G [02:26<02:11, 77.4MB/s]
# i = load_dataset("wikipedia", "20220301.it")
# v = load_dataset("wikipedia", "20220301.vi")
# DatasetDict({
#     train: Dataset({
#         features: ['id', 'url', 'title', 'text'],
#         num_rows: 1743035
#     })
# })

e['train'][3]
# {'id': '290', 'url': 'https://en.wikipedia.org/wiki/A', 'title': 'A', 'text': 'A, or a, is the first letter and the first vowel of the modern English alphabet and the ISO basic Latin alphabet. Its name in English is a (pronounced ), plural aes. It is similar in shape to the Ancient Greek letter alpha, from which it derives. The uppercase version consists of the two slanting sides ...'}

from transformers import AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained('bert-base-cased')

def tokenize_function(examples):
    return tokenizer(examples['text'], padding='max_length', truncation=True)

dataset = dataset.map(tokenize_function, batched=True)

```

The list of pre-processed subsets is:
- "20220301.de"
- "20220301.en"
- "20220301.fr"
- "20220301.frr"
- "20220301.it"
- "20220301.simple"


- - -


RAW DATA

https://dumps.wikimedia.org/viwiki/20230220

https://dumps.wikimedia.org/viwiki/20230220/viwiki-20230220-pages-articles-multistream-index.txt.bz2

=>

https://dumps.wikimedia.org/enwiki/20230220

https://dumps.wikimedia.org/enwiki/20230220/enwiki-20230220-pages-articles-multistream-index.txt.bz2

