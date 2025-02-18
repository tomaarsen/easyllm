# Prompt utilities

The `prompt_utils`  module contains functions to assist with converting Message's Dictionaries into prompts that can be used with `ChatCompletion` clients. 

Supported prompt formats:

* [Llama 2](#llama-2-chat-builder)
* [Vicuna](#vicuna-chat-builder)
* [Hugging Face ChatML](#hugging-face-chatml-builder)
* [WizardLM](#wizardlm-chat-builder)
* [StableBeluga2](#stablebeluga2-chat-builder)
* [Open Assistant](#open-assistant-chat-builder)


## Set prompt builder for client

```python
from easyllm.clients import huggingface
from easyllm.prompt_utils import build_llama2_prompt

huggingface.prompt_builder = build_llama2_prompt
```

## Llama 2 Chat builder 

Creates LLama 2 chat prompt for chat conversations. Learn more in the [Hugging Face Blog on how to prompt Llama 2](https://huggingface.co/blog/llama2#how-to-prompt-llama-2). If a `Message` with an unsupported `role` is passed, an error will be thrown.

Example Models: 

* [meta-llama/Llama-2-70b-chat-hf](https://huggingface.co/meta-llama/Llama-2-70b-chat-hf)

```python
from easyllm.prompt_utils import build_llama2_prompt

messages=[
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "Explain asynchronous programming in the style of the pirate Blackbeard."},
]
prompt = build_llama2_prompt(messages)
```


## Vicuna Chat builder 

Creats a Vicuna prompt for a chat conversation. If a `Message` with an unsupported `role` is passed, an error will be thrown. [Reference](https://github.com/lm-sys/FastChat/blob/main/docs/vicuna_weights_version.md#prompt-template)

Example Models: 

* [ehartford/WizardLM-13B-V1.0-Uncensored](https://huggingface.co/ehartford/WizardLM-13B-V1.0-Uncensored)


```python
from easyllm.prompt_utils import build_vicuna_prompt

messages=[
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "Explain asynchronous programming in the style of the pirate Blackbeard."},
]
prompt = build_vicuna_prompt(messages)
```

## Hugging Face ChatML builder 

Creates a Hugging Face ChatML prompt for a chat conversation. The Hugging Face ChatML has different prompts for different Example Models, e.g. StarChat or Falcon. If a `Message` with an unsupported `role` is passed, an error will be thrown. [Reference](https://huggingface.co/HuggingFaceH4/starchat-beta)

Example Models: 
* [HuggingFaceH4/starchat-beta](https://huggingface.co/HuggingFaceH4/starchat-beta)

### StarChat

```python
from easyllm.prompt_utils import build_chatml_starchat_prompt

messages=[
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "Explain asynchronous programming in the style of the pirate Blackbeard."},
]
prompt = build_chatml_starchat_prompt(messages)
```

### Falcon

```python
from easyllm.prompt_utils import build_chatml_falcon_prompt

messages=[
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "Explain asynchronous programming in the style of the pirate Blackbeard."},
]
prompt = build_chatml_falcon_prompt(messages)
```

## WizardLM Chat builder 

Creates a WizardLM prompt for a chat conversation. If a `Message` with an unsupported `role` is passed, an error will be thrown. [Reference](https://github.com/nlpxucan/WizardLM/blob/main/WizardLM/src/infer_wizardlm13b.py#L79)

Example Models:

* [WizardLM/WizardLM-13B-V1.2](https://huggingface.co/WizardLM/WizardLM-13B-V1.2)

```python
from easyllm.prompt_utils import build_wizardlm_prompt

messages=[
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "Explain asynchronous programming in the style of the pirate Blackbeard."},
]
prompt = build_wizardlm_prompt(messages)
```

## StableBeluga2 Chat builder 

Creates StableBeluga2 prompt for a chat conversation. If a `Message` with an unsupported `role` is passed, an error will be thrown. [Reference](https://huggingface.co/stabilityai/StableBeluga2)

```python
from easyllm.prompt_utils import build_stablebeluga_prompt

messages=[
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "Explain asynchronous programming in the style of the pirate Blackbeard."},
]
prompt = build_stablebeluga_prompt(messages)
```

## Open Assistant Chat builder 

Creates Open Assistant ChatML template. Uses `<|prompter|>`, `</s>`, `<|system|>`, and `<|assistant>` tokens. If a . If a `Message` with an unsupported `role` is passed, an error will be thrown. [Reference](https://huggingface.co/OpenAssistant/llama2-13b-orca-8k-33192)

Example Models:

* [OpenAssistant/llama2-13b-orca-8k-3319](https://huggingface.co/OpenAssistant/llama2-13b-orca-8k-33192)

```python
from easyllm.prompt_utils import build_open_assistant_prompt

messages=[
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "Explain asynchronous programming in the style of the pirate Blackbeard."},
]
prompt = build_open_assistant_prompt(messages)
```

