## https://huggingface.co/datasets/wikipedia

Wikipedia dataset containing cleaned articles of all languages. The datasets are built from the Wikipedia dump (https://dumps.wikimedia.org/) with one split per language. Each example contains the content of one full Wikipedia article with cleaning to strip markdown and unwanted sections (references, etc.).

The articles are parsed using the mwparserfromhell tool.

To load this dataset you need to install Apache Beam and mwparserfromhell first:

```sh
pip3 install apache_beam mwparserfromhell
```

```py
from datasets import load_dataset
load_dataset("wikipedia", "20220301.en")
# Downloading:  50%|██████████████████████████▍                       | 10.1G/20.3G [02:26<02:11, 77.4MB/s]
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

