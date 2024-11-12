# GraphRAG demo
This repo contains code to demonstrate usage of microsofts GraphRAG.

## Requirements
This code uses python 3.12. The requirements file outline the non-standard libraries required to run this piece of code.

## Set up environment variables


## Firstly - get some data
get-news-data.ipynb contains code to get some current news data using Fundus and dumps it in a local folder.

## Optional step - vectorise data and inspect with Qdrant
...


## GraphRAG
This largely follows the microsoft documentation that can be found below, but with a couple of changes for our usecase;

https://microsoft.github.io/graphrag/get_started/

### Initialize project 
Initialize the project using the following command:

`python -m graphrag.index --init --root .`

### Change configurations
Go into the settings.yaml file and change a couple of fields:

The default model is gpt-4-turbo. This is rather slow and expensive for the time being, therefore I suggest changing this to the gpt-4o-mini model.

`model: gpt-4o-mini`

The default folder graphrag looks for data is in a folder called 'inputs', however, we called our folder 'data' therefore we need to change this in the settings.yaml file.

```
input:
  base_dir: "data"
```

### Index documents
In order to structure your data for querying, we need to index them using the following command:

`python -m graphrag.index --root .`

### Query data

```
graphrag query \
--root . \
--method global \
--query "Que son las noticias principales de hoy?"
```

```
graphrag query \
--root . \
--method global \
--query "Que son las temas mas polemicas en las noticias de hoy?"
```

```
graphrag query \
--root . \
--method global \
--community-level 3 \
--query "Que son las temas mas polemicas en las noticias de hoy?"
```