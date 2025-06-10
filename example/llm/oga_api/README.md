# Ryzen AI LLM - Onnxruntime GenAI

Ryzen AI Software includes support for deploying LLMs on Ryzen AI PCs using the ONNX Runtime generate() API (OGA). 

## Pre-optimized Models

AMD provides a set of pre-optimized LLMs ready to be deployed with Ryzen AI Software and the supporting runtime for hybrid and NPU execution. These models can be found on Hugging Face: 

### Published models: 
- [Ryzen AI Hybrid models.](https://huggingface.co/collections/amd/ryzenai-14-llm-hybrid-models-67da31231bba0f733750a99c)
- [Ryzen AI NPU models.](https://huggingface.co/collections/amd/ryzenai-13-llm-npu-models-6759f510b8132db53e044aaf)

## Ryzen AI Installation

- The steps for installing Ryzen AI along with it's requirement can be found in the Official Ryzen AI Software documantion page here - https://ryzenai.docs.amd.com/en/latest/inst.html

## Steps to compile and run LLM example.
- Activate Ryzen AI environment:
```
conda activate ryzen-ai-1.5.0
```
- Download the model: This example uses the Llama-2-7b-chat model.
```
#hyrbid model:
git clone https://huggingface.co/amd/Llama-2-7b-chat-hf-awq-g128-int4-asym-fp16-onnx-hybrid

#npu model:
git clone https://huggingface.co/amd/Llama2-7b-chat-awq-g128-int4-asym-bf16-onnx-ryzen-strix
```
- Clone the RyzenAI-SW repository:
```
git clone https://github.com/amd/RyzenAI-SW
```
- Navigate to OGA_API folder:
```
cd path\to\RyzenAI-SW\example\llm\oga_api
```
- Copy necessary DLLs and onnxruntime-genai.lib:
```
xcopy /I "%RYZEN_AI_INSTALLATION_PATH%\deployment\*" libs
xcopy /I "%RYZEN_AI_INSTALLATION_PATH%\LLM\onnxruntime_genai\lib\onnxruntime-genai.lib" libs
```
- Compile and build the code:
```
   mkdir build
   cd build
   cmake .. -A x64
   cmake --build . --config Release
   cd bin\Release
```
- Execute code:
```
.\example.exe -m "<path_to_model>"
```
- Example command
```
.\example.exe -m "path\to\Llama-2-7b-chat-hf-awq-g128-int4-asym-fp16-onnx-hybrid"
```


# Copyright

Copyright(C) 2025 Advanced Micro Devices, Inc. All rights reserved.
