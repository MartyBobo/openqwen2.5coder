# OpenQwen2.5Coder Setup Guide

This document provides step-by-step instructions for setting up and running OpenQwen2.5Coder using Ollama on Windows via WSL.

## Windows Setup with WSL2

### Step 1: Install WSL2 on Windows
1. Open PowerShell as Administrator
2. Run the following command:
   ```powershell
   wsl --install
   ```
3. Restart your computer when prompted
4. Follow the setup steps for Ubuntu when it launches

### Step 2: Install Ollama in WSL Ubuntu
1. Open your WSL Ubuntu terminal
2. Install Ollama using the installation script:
   ```bash
   curl -fsSL https://ollama.com/install.sh | sh
   ```

### Step 3: Configure Ollama Server
1. Check if Ollama is already running:
   ```bash
   ps aux | grep ollama
   ```
   
2. If Ollama processes are running, stop them:
   ```bash
   # Replace <PID> with the actual process ID
   sudo kill <PID>
   ```

3. Find your WSL IP address:
   ```bash
   ip addr show eth0 | grep "inet " | awk '{print $2}' | cut -d/ -f1
   ```

4. Set the Ollama host environment variable:
   ```bash
   export OLLAMA_HOST=<YOUR_WSL_IP>
   ```

5. Start the Ollama server:
   ```bash
   ollama serve
   ```
   
   *Note: Keep this terminal open with the server running.*

### Step 4: Use Ollama Client in a New Terminal
1. Open a new WSL Ubuntu terminal

2. Set the Ollama host environment variable in this new terminal:
   ```bash
   export OLLAMA_HOST=<YOUR_WSL_IP>
   ```

3. Pull the Qwen2.5 Coder model:
   ```bash
   # Pull the Qwen2.5 Coder 14B model with 4-bit quantization
   ollama pull qwen2.5-coder:14b-instruct-q4_K_M
   ```

4. Run the model:
   ```bash
   ollama run qwen2.5-coder:14b-instruct-q4_K_M
   ```

### Step 5: Configure Windows to Access Ollama
1. In Windows, open Command Prompt or PowerShell
   
2. Set the Ollama host environment variable:
   ```
   set OLLAMA_HOST=<YOUR_WSL_IP>:11434
   ```
   
3. For permanent setup, add a system environment variable:
   - Press Win + R, type "sysdm.cpl", press Enter
   - Go to the "Advanced" tab and click "Environment Variables"
   - Add a new system variable named `OLLAMA_HOST` with value `<YOUR_WSL_IP>:11434`

## Recommended Models for Different Hardware

### For 12GB VRAM (e.g., RTX 4070 SUPER):
- `qwen2.5-coder:14b-instruct-q4_K_M` - Excellent for coding tasks
- `mistral:7b-instruct-q4_K_M` - Great general-purpose model
- `llama3:8b-instruct-q4_K_M` - Strong all-around performer

### For 8GB VRAM:
- `mistral:7b-instruct-q4_K_M`
- `llama3:8b-instruct-q4_0` (basic quantization)
- `phi-3:mini-q4_K_M`

### For 4GB VRAM:
- `phi-3:mini-q4_0`
- `gemma:7b-instruct-q4_0`

## Additional Ollama Commands

### Check available models:
```bash
ollama list
```

### View running models:
```bash
ollama ps
```

### Remove a model:
```bash
ollama rm model_name
```

## Client Connection Example

You can connect to your running Ollama instance using this Python script:

```python
import requests
import json

def query_qwen_coder(prompt, server_url="http://localhost:11434"):
    endpoint = f"{server_url}/api/generate"
    
    payload = {
        "model": "qwen2.5-coder:14b-instruct-q4_K_M",
        "prompt": prompt,
        "stream": False
    }
    
    headers = {
        "Content-Type": "application/json"
    }
    
    response = requests.post(endpoint, headers=headers, data=json.dumps(payload))
    
    if response.status_code == 200:
        return response.json()["response"]
    else:
        return f"Error: {response.status_code} - {response.text}"

if __name__ == "__main__":
    prompt = "Write a function to reverse a linked list in Java"
    result = query_qwen_coder(prompt)
    print(result)
```

## Advanced Setup (Optional)

### Creating a Permanent Configuration

1. Open your `.bashrc` file in an editor:
   ```bash
   nano ~/.bashrc
   ```

2. Add the following line at the end of the file:
   ```bash
   export OLLAMA_HOST=$(ip addr show eth0 | grep "inet " | awk '{print $2}' | cut -d/ -f1)
   ```

3. Save and exit (Ctrl+O, Enter, Ctrl+X)

4. Apply the changes:
   ```bash
   source ~/.bashrc
   ```

## Troubleshooting

### "Address already in use" error

If you see this error:
```
Error: listen tcp 127.0.0.1:11434: bind: address already in use
```

Follow these steps:
1. Find the process using the port:
   ```bash
   sudo lsof -i :11434
   ```

2. Kill the process:
   ```bash
   sudo kill <PID>
   ```

3. Start again with the correct host:
   ```bash
   export OLLAMA_HOST=<YOUR_WSL_IP>
   ollama serve
   ```

### Can't connect from Windows
1. Check Windows Firewall settings to allow connections to port 11434
2. Verify the WSL IP hasn't changed (it can change after restarting)
3. Confirm you're including the port in the Windows environment variable

### Model running out of memory
1. Try a smaller model
2. Use a more aggressive quantization (q4_0 instead of q8_0)
3. Reduce context length if your model allows it