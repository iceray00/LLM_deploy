







## In Terminal 1
- This process is responsible for listening to the memory consumption ratio of CUDA
```bash
nvidia-smi -l 1
```

## In Terminal 2
- Run Ollama serve
```bash
ollama serve
```

## In Terminal 3
- This process is responsible for running the `Open-WebUI `
```bash
open-webui serve
```

## In Terminal 4
- This process is responsible for running Ngrok for Intranet penetration
```bash
ngrok http 8080
```

**Be sure to turn off Academic acceleration**













