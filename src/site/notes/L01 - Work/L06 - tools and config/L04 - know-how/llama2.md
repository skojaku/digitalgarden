---
{"dg-publish":true,"permalink":"/l01-work/l06-tools-and-config/l04-know-how/llama2/","dgPassFrontmatter":true}
---


# llama2
updated: 2023-12-03 Using 

# Using HuggingFace

## Set up

1. Sign in/up HuggingFace 
2. Generate the HuggingFace API Key.
3. Go to [meta-llama/Llama-2-7b-chat-hf](https://huggingface.co/meta-llama/Llama-2-7b-chat-hf)to register on Meta. The model will be available in one-two days.
4. [Install PyTorch](https://pytorch.org/) and `transformers` library
5. Make sure that your version of the Pytorch is consistent with the cuda version in the system by typing `nvcc --version` and `python -c "import torch;print(torch.version.cuda)"` (see also the cuda set up to configure nvcc if nvcc is not found on your system).
- Install bitesandbytes for quantization: `pip install bitsandbytes-cuda112 bitsandbytes`.

## Inference
```python
import torch
import transformers
from torch import cuda, bfloat16

# Define the model ID and Hugging Face authentication token
model_id = "TheBloke/Llama-2-7B-Chat-GPTQ"
hf_auth = <YOUR HAGGINGFACE API KEY>

# Determine the device to use for computation (GPU if available, otherwise CPU)
device = f"cuda:{cuda.current_device()}" if cuda.is_available() else "cpu"
device_name = torch.cuda.get_device_name()
print(f"Using device: {device} ({device_name})")

# Configure the BitsAndBytes quantization settings
bnb_config = transformers.BitsAndBytesConfig(
    load_in_4bit=True,
    bnb_4bit_quant_type="nf4",
    bnb_4bit_use_double_quant=True,
    bnb_4bit_compute_dtype=bfloat16,
)

# Load the model configuration
model_config = transformers.AutoConfig.from_pretrained(model_id, use_auth_token=hf_auth)

# Load the model
model = transformers.AutoModelForCausalLM.from_pretrained(
    model_id,
    trust_remote_code=True,
    config=model_config,
    quantization_config=bnb_config,
    device_map="auto",
    use_auth_token=hf_auth,
)
model.eval()  # Set the model to evaluation mode

# Load the tokenizer
tokenizer = transformers.AutoTokenizer.from_pretrained(model_id, use_auth_token=hf_auth)

# Define the text generation pipeline
generate_text = transformers.pipeline(
    model=model,
    tokenizer=tokenizer,
    return_full_text=True,
    task="text-generation",
    temperature=0.1,  # 'randomness' of outputs, 0.0 is the min and 1.0 the max
    max_new_tokens=2024,  # max number of tokens to generate in the output
    repetition_penalty=1.1,  # without this output begins repeating
)

# Generate text and print the result
res = generate_text("Explain to me the difference between nuclear fission and fusion.")
print(res[0]["generated_text"])
```

# Using llama2.cpp
## Set up 

```bash
mamba create -n llama2test
mamba activate llama2test
pip install llama-cpp-python
mamba install huggingface_hub    
```


## Model
Multiple versions of llama2 can be found in the following page. 
[TheBloke (Tom Jobbins)](https://huggingface.co/TheBloke)

Then, download the model by using huggingface command. For example, 

```bash
huggingface-cli download TheBloke/Llama-2-7B-GGUF llama-2-7b.Q4_K_M.gguf --local-dir . --local-dir-use-symlinks False
```
 (Change the model name and output file name appropriately)

> [!Note About model files]
> There are two formats for the llama2 models, namely ggmlv and gguf format. ggmlv is a legacy format. So use gguf format. 

## Inference 
```python 
from llama_cpp import Llama

LLM = Llama(
    model_path="llama-2-7b.Q4_K_M.gguf"
)

# Prompt
prompt = "Q: What is the hight of mount Fuzi? A:"

# generate a response (takes several seconds)
output = LLM(prompt)

# display the response
print(output["choices"][0]["text"])
```

# Reference
[Run Llama 2 Locally with Python](https://swharden.com/blog/2023-07-29-ai-chat-locally-with-python/)
