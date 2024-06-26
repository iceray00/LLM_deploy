
## _1_



Download the open source model from Hugging Face with `.gguf `as the suffix

For example: (Take Alibaba open source Qwen1.5-7B model as an example):

```bash
wget https://huggingface.co/Qwen/Qwen1.5-7B-Chat-GGUF/resolve/main/qwen1_5-7b-chat-q4_0.gguf?download=true
```

In the same folder, create a `Modelfile` file:
```bash
vim Modelfile
```
### Create a Modelfile:
```
FROM ./[Model_q_*].gguf

# set the temperature to 1 [higher is more creative, lower is more coherent]
PARAMETER temperature 0.7
PARAMETER top_p 0.8
PARAMETER repeat_penalty 1.05
PARAMETER top_k 20

TEMPLATE """{{ if and .First .System }}<|im_start|>system
{{ .System }}<|im_end|>
{{ end }}<|im_start|>user
{{ .Prompt }}<|im_end|>
<|im_start|>assistant
{{ .Response }}"""

# set the system message
SYSTEM """
You are a helpful assistant.
"""

```


Change the ollama's `models` installation default path:
```
export OLLAMA_MODELS=/root/autodl-tmp/models
echo 'export OLLAMA_MODELS=/root/autodl-tmp/models' >> ~/.bashrc
source ~/.bashrc
```

## Download **ollama** ：
```
curl -fsSL https://ollama.com/install.sh | sh

```


### Start ollama serve in one Terminal:
```
ollama serve
```

### create `.gguf` model loading by ollama
Use ollama's `create` directive to customize the load local `.gguf` format large model:
```
ollama create [Model_name] -f ./Modelfile
```

### List models on your computer

```
ollama list
ollama ls
```


### Remove a model

```
ollama rm llama3
```

### Copy a model

```
ollama cp llama3 my-model
```

### Multiline input

For multiline input, you can wrap text with `"""`:

```
>>> """Hello,
... world!
... """
I'm a basic program that prints the famous "Hello, world!" message to the console.
```

### Multimodal models

```
>>> What's in this image? /Users/jmorgan/Desktop/smile.png
The image features a yellow smiley face, which is likely the central focus of the picture.
```

### Pass the prompt as an argument

```
$ ollama run llama3 "Summarize this file: $(cat README.md)"
 Ollama is a lightweight, extensible framework for building and running language models on the local machine. It provides a simple API for creating, running, and managing models, as well as a library of pre-built models that can be easily used in a variety of applications.
```

### Start Ollama

`ollama serve` is used when you want to start ollama without running the desktop application.

## Building

See the [developer guide](https://github.com/ollama/ollama/blob/main/docs/development.md)

### Running local builds

Next, start the server:

```
./ollama serve
```

Finally, in a separate shell, run a model:

```
./ollama run llama3
```

## REST API

Ollama has a REST API for running and managing models.

### Generate a response

```
curl http://localhost:11434/api/generate -d '{
  "model": "llama3",
  "prompt":"Why is the sky blue?"
}'
```

### Chat with a model

```
curl http://localhost:11434/api/chat -d '{
  "model": "llama3",
  "messages": [
    { "role": "user", "content": "why is the sky blue?" }
  ]
}'
```


## attention:
- 不要在ollama create之前安装nodejs，不然会不够空间
```

```


















