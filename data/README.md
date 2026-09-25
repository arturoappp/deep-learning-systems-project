# Data access

The notebook downloads the six language files it needs from the public repository of
*A massively parallel corpus: the Bible in 100 languages* (Christodoulopoulos & Steedman, 2015),
licensed CC0 1.0, pinned to commit `44e5fca1bfb369a5da2ee23ebc6f421c88489c5c`:

```
https://raw.githubusercontent.com/christos-c/bible-corpus/44e5fca1bfb369a5da2ee23ebc6f421c88489c5c/bibles/<Language>.xml
```

Languages used: Spanish, Portuguese, Italian, French, Romanian and Latin (about 35 MB in total).
The files are cached in `data/raw/` on the first run. They are not committed to this repository because
some of the underlying translations are still under copyright; the corpus is distributed for research use.
