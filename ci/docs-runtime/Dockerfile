# Temporary CI docs-validation runtime for NVIDIA-NeMo/Speech.
# Reproduces docs/update_docs_docker.sh: base python:3.10, uv==0.11.14,
# uv sync --locked --group docs, then make -C docs html / linkcheck.
# Runtime-only tooling image; not part of any repair PR.
FROM 766267172432.dkr.ecr.us-east-2.amazonaws.com/dockerhub/library/python:3.10
RUN pip install --no-cache-dir uv==0.11.14
RUN apt-get update && apt-get install -y --no-install-recommends make jq ca-certificates \
    && rm -rf /var/lib/apt/lists/*
WORKDIR /src
COPY . /src
RUN uv sync --locked --group docs
CMD ["bash", "-c", "uv run make -C docs clean html"]
