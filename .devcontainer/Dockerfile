FROM julia:1.11

RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 \
    python3-pip \
    python3-venv \
    git \
    && rm -rf /var/lib/apt/lists/*

# Use a venv to avoid PEP 668 "externally-managed-environment" errors
ENV VIRTUAL_ENV=/opt/venv
RUN python3 -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

RUN pip install --no-cache-dir jupyter matplotlib

# Pre-install IJulia so Jupyter can find the Julia kernel
RUN julia -e 'using Pkg; Pkg.add("IJulia")'

WORKDIR /workspace
