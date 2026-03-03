# Model serving on Crusoe Managed Kubernetes using vllm with and without Ray Serve  

This repo contains examples of serving models on Crusoe Managed Kubernetes

The DeepSeek example use Ray Serve for multi-node vllm serving of DeepSeek R1 70B  

The QWEN 3.5 example directly runs VLLM in a custom container but only works on a single node. Because this is is such a new model,
we're still trying to get it working as a Ray Service, at which point multi-node serving will be possible.
