# For use with GB200, replace platform tag with linux/arm64
FROM --platform=linux/amd64 nvidia/cuda:12.8.0-devel-ubuntu22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    python3.10 \
    python3.10-dev \
    python3-pip \
    git \
    curl \
    && rm -rf /var/lib/apt/lists/*

RUN update-alternatives --install /usr/bin/python python /usr/bin/python3.10 1

RUN python -m pip install --upgrade pip setuptools wheel

RUN pip install vllm --pre --extra-index-url https://wheels.vllm.ai/nightly

# Expose the default vLLM API server port
EXPOSE 8000

ENTRYPOINT ["vllm", "serve", "--host", "0.0.0.0", "--port", "8000"]
