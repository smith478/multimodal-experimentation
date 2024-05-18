# multimodal-experimentation
Experimentations with multimodal models

## Getting started

### Docker

The docker image can be built using `./Dockerfile`. You can build it using the following command, run from the root directory

```bash
docker build --build-arg WB_API_KEY=<your_api_key> . -f Dockerfile --rm -t llm-finetuning:latest
```

### Run docker container

First navigate to this repo on your local machine. Then run the container:

```bash
docker run --gpus all --name multimodal-experimentation -it --rm -p 8888:8888 -p 8501:8501 -p 8000:8000 --entrypoint /bin/bash -w /multimodal-experimentation -v $(pwd):/multimodal-experimentation llm-finetuning:latest
```

### Run jupyter from the container
Inside the Container:
```bash
jupyter lab --ip 0.0.0.0 --no-browser --allow-root --NotebookApp.token=''
```

Host machine access this url:
```bash
localhost:8888/<YOUR TREE HERE>
```

### Run streamlit from the container
Inside the container:
```bash
streamlit run app.py
```

Host machine:
```bash
localhost:8501
```

## TODO 

- Look at implementing these:
    - https://huggingface.co/google/paligemma-3b-pt-224 (or larger input image size)
    - https://huggingface.co/visheratin/MC-LLaVA-3b
    - https://huggingface.co/llava-hf/llava-1.5-7b-hf