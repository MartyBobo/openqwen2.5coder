# OpenQwen2.5Coder

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 🚀 Overview

OpenQwen2.5Coder is an open-source project that leverages the Qwen2.5 language model for code generation, completion, and assistance tasks. This repository contains the necessary files and instructions to set up and run the Qwen2.5 LLM using Ollama for coding assistance.

## 🌟 Features

- **Containerized LLM Setup**: Run Qwen2.5 in an isolated Docker container
- **Code Generation**: Generate code based on natural language descriptions
- **Code Completion**: Get intelligent code suggestions and completions
- **Multi-language Support**: Supports all major programming languages
- **Low Resource Requirements**: Optimized to run on consumer hardware
- **Custom Prompts**: Create and share prompt templates for specific tasks

## 🛠️ Requirements

- Docker or Ollama installed on your system
- 16GB RAM minimum (32GB recommended)
- 50GB free disk space
- NVIDIA GPU with CUDA support (optional, for accelerated inference)

## 📦 Installation

Please refer to our [COMMANDS.md](COMMANDS.md) file for detailed installation and setup instructions for both Docker and Ollama.

## ⚙️ Configuration

Create a `config.toml` file in your config directory:

```toml
[llm]
model = "qwen2.5"
api_key = ""  # Leave empty for local deployment
max_tokens = 4096
temperature = 0.2

[server]
port = 3000
host = "0.0.0.0"
```

## 🔧 Usage

Once the server is running, you can access the OpenQwen2.5Coder through the API:

```bash
curl -X POST http://localhost:11434/api/generate \
  -H "Content-Type: application/json" \
  -d '{"model": "qwen2.5-coder:14b-instruct-q4_K_M", "prompt": "Write a function that sorts an array in JavaScript"}'
```

## 📚 Examples

### Code Generation

```
Write a Python function to find the longest common subsequence of two strings
```

### Bug Fixing

```
Fix this code:

def fibonacci(n):
    if n <= 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fibonacci(n-1) + fibonacci(n)
```

### Code Explanation

```
Explain the following code:

const memoize = fn => {
  const cache = {};
  return (...args) => {
    const key = JSON.stringify(args);
    if (!(key in cache)) {
      cache[key] = fn(...args);
    }
    return cache[key];
  };
};
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Contact

MartyBobo - [@martybobo](https://github.com/MartyBobo)

Project Link: [https://github.com/MartyBobo/openqwen2.5coder](https://github.com/MartyBobo/openqwen2.5coder)