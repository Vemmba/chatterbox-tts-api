<div align="center">

# 🎙️ Chatterbox TTS API

**FastAPI-powered REST API for [Chatterbox TTS](https://github.com/resemble-ai/chatterbox)**
OpenAI-compatible endpoints · Voice cloning · Multilingual · React frontend

[![GitHub stars](https://img.shields.io/github/stars/Vemmba/chatterbox-tts-api?style=social)](https://github.com/Vemmba/chatterbox-tts-api)
[![GitHub forks](https://img.shields.io/github/forks/Vemmba/chatterbox-tts-api)](https://github.com/Vemmba/chatterbox-tts-api)
[![GitHub issues](https://img.shields.io/github/issues/Vemmba/chatterbox-tts-api)](https://github.com/Vemmba/chatterbox-tts-api/issues)
[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL--3.0-blue)](LICENSE)

Maintained by **[Vemmba](https://github.com/Vemmba)** · Fork of [travisvn/chatterbox-tts-api](https://github.com/travisvn/chatterbox-tts-api)

</div>

---

## ✨ Features

- 🚀 **OpenAI-compatible API** — drop-in replacement for OpenAI's TTS endpoint
- 🌍 **Multilingual** — speech generation in 22 languages with language-aware voice cloning
- 🎭 **Voice cloning** — use your own audio samples for personalized speech
- 🎤 **Voice library** — upload, manage, and use custom voices by name
- 📝 **Long-text handling** — automatic chunking plus background job processing
- 📊 **Real-time status** — streaming progress, statistics, and request history
- 🎨 **React frontend** — optional, ready-to-use web interface
- 🐳 **Docker ready** — CPU / GPU / full-stack compose files included
- 🧠 **Memory management** — monitoring and automatic cleanup
- 📚 **Auto docs** — interactive documentation at `/docs` and `/redoc`

## ⚡ Quick Start

```bash
git clone https://github.com/Vemmba/chatterbox-tts-api
cd chatterbox-tts-api
uv sync
uv run main.py
```

> [!TIP]
> Install [uv](https://docs.astral.sh/uv/) with `curl -LsSf https://astral.sh/uv/install.sh | sh` (or `powershell -c "irm https://astral.sh/uv/install.ps1 | iex"` on Windows).

The API starts on `http://localhost:4123` — open `/docs` for interactive documentation.

### Requirements

- Python **3.11** (exactly — `requires-python >=3.11,<3.12`)
- CUDA-capable GPU recommended (see the note on non-CUDA setups below)

### Configuration

Copy `.env.example` to `.env` and adjust as needed:

```bash
cp .env.example .env
```

Key options include host/port, chunk settings, memory limits, and voice library paths.

## 🐳 Docker

```bash
# CPU
docker compose -f docker/docker-compose.cpu.yml up --build

# GPU
docker compose -f docker/docker-compose.gpu.yml up --build

# Full stack (API + frontend)
docker compose -f docker/docker-compose.yml --profile frontend up --build
```

See [docs/DOCKER_README.md](docs/DOCKER_README.md) for details.

## 🖥️ Frontend

An optional React (Vite + Tailwind) web UI lives in [`frontend/`](frontend/). Run it via the full-stack Docker profile above, or develop it standalone with `npm install && npm run dev` inside `frontend/`.

## 📖 Documentation

| Doc | Contents |
| --- | --- |
| [docs/API_README.md](docs/API_README.md) | API overview and examples |
| [docs/STREAMING_API.md](docs/STREAMING_API.md) | Streaming endpoints |
| [docs/STATUS_API.md](docs/STATUS_API.md) | Status & statistics API |
| [docs/VOICE_LIBRARY_MANAGEMENT.md](docs/VOICE_LIBRARY_MANAGEMENT.md) | Voice upload & management |
| [docs/MULTILINGUAL.md](docs/MULTILINGUAL.md) | Multilingual support |
| [CHANGELOG.md](CHANGELOG.md) | Release history |

## ⚠️ Known Issues

- `resemble-ai/chatterbox` is currently broken for **non-CUDA** setups (see [chatterbox issues](https://github.com/resemble-ai/chatterbox/issues)). This fork uses the multilingual build via `chatterbox-tts @ git+https://github.com/travisvn/chatterbox-multilingual.git@exp`; for non-CUDA machines use the `stable` branch.
- Python 3.11 is required — other versions are not supported by the upstream models.

## 📜 License & Credits

This project is licensed under the **GNU AGPL-3.0** — see [LICENSE](LICENSE).

This is a personal fork maintained by [Vemmba](https://github.com/Vemmba), based on [travisvn/chatterbox-tts-api](https://github.com/travisvn/chatterbox-tts-api) by Travis Van Nimwegen, which wraps the [Chatterbox](https://github.com/resemble-ai/chatterbox) model by Resemble AI.
