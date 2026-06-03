# 🐳 ROCm Docker Setup

One-click Docker setup for AMD ROCm development environment.

## Quick Start

```bash
# Clone repo
git clone https://github.com/dickcongwe/rocm-docker-setup.git
cd rocm-docker-setup

# Build and run
docker compose up -d

# Access Jupyter
open http://localhost:8888
```

## Available Images

| Image | Purpose | Size |
|-------|---------|------|
| `rocm-pytorch` | PyTorch training | 12GB |
| `rocm-tensorflow` | TensorFlow training | 14GB |
| `rocm-jax` | JAX development | 10GB |
| `rocm-minimal` | Base ROCm env | 6GB |

## Docker Compose Services

```yaml
services:
  jupyter:
    build: ./jupyter
    ports: ["8888:8888"]
    devices:
      - /dev/kfd:/dev/kfd
      - /dev/dri:/dev/dri
  
  tensorboard:
    build: ./tensorboard
    ports: ["6006:6006"]
  
  vscode:
    build: ./vscode
    ports: ["8080:8080"]
```

## Requirements

- AMD GPU (RDNA 2+ or CDNA)
- Ubuntu 22.04+
- Docker 24.0+
- ROCm 5.7+ kernel modules

## License

MIT
