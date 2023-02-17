Sample created with

```
$ for f in *; do head -n 100 "${f}" > "${f%.*}_sample.${f#*.}"; done
```

Full data

```
$ wc -l *
   2937410 contexts_used.jsonl
      7592 datasets.jsonl
    208597 datasets_to_papers.csv
     13071 datasets_to_tasks.csv
         7 method_areas.jsonl
      2026 methods.jsonl
      2511 methods_to_collections.csv
      1830 methods_to_datasets.csv
    312291 methods_to_papers.csv
     22189 models.jsonl
    102779 models_to_papers.csv
    340965 papers.jsonl
    473087 papers_to_papers.csv
      5259 tasks.jsonl
    506792 tasks_to_papers.csv
      3097 tasks_to_subtasks.csv
   4939503 total
```
