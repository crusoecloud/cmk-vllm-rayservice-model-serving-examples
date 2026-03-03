# QWEN 3.5 35B on vllm

This folder contains a deployment that pulls a vllm image that was created using the vllm nightly build on 3/2/2026. Prerequisites are
a CMK cluster with a working storageclass (run `kubectl get sc` to check if you have one; if not, check the [CMK storage/CSI docs](https://docs.crusoecloud.com/orchestration/cmk/cmk-addons)
and a node with available GPU resources (adapt the yaml to suit your number of available GPUs).  

To deploy the yaml: `kubectl apply -f vllm-deployment.yaml'  
After the vllm pod starts up, tail its logs to monitor its progress at downloading the model weights and starting vllm. First time around this takes about 20 minutes but the weights
are cached onto the PVC so subsequent restarts are much quicker.

You might want to build your own container image to pull in a more recent version of vllm (which you can do with `docker build -t qwen3_5-vllm:v2 .` or similar) or simply replace
the custom Docker image with a published vllm image such as vllm/vllm-openai:cu130-nightly.
