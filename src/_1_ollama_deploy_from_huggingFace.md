
## _1_


### 1.1 Download model from HuggingFace
Download the open source model from Hugging Face with `.gguf `as the suffix

For example: (Take Alibaba open source Qwen1.5-7B model as an example):

```bash
wget https://huggingface.co/Qwen/Qwen1.5-7B-Chat-GGUF/resolve/main/qwen1_5-7b-chat-q4_0.gguf?download=true
```

### 1.2 Create a Modelfile:
In the same folder, create a `Modelfile` file:
```bash
vim Modelfile
```

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


## 2 

### 2.1 Change default path
Change the ollama's `models` installation default path:
```
export OLLAMA_MODELS=/root/autodl-tmp/models
echo 'export OLLAMA_MODELS=/root/autodl-tmp/models' >> ~/.bashrc
source ~/.bashrc
```


### 2.2 Download **ollama** ：
```
curl -fsSL https://ollama.com/install.sh | sh
```


### 2.3 Start ollama serve in one Terminal:
```
ollama serve
```

### 2.4 create `.gguf` model loading by ollama
Use ollama's `create` directive to customize the load local `.gguf` format large model:
```
ollama create [Model_name] -f ./Modelfile
```

## 3 Usage

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
ollama serve
```

Finally, in a separate shell, run a model:

```
ollama run llama3
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
- Do not install `nodejs` before `ollama create`, as you will run out of space

* A cursory test shows that `ollama create` is about 1.5-2 times the maximum limit of the model


















