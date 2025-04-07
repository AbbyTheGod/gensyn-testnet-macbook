To run the Gensyn RL Swarm node on your MacBook, follow this step-by-step guide tailored for macOS:

---

## **Step 1: Install Required Tools**
Since macOS does not support `apt-get`, you will need to use **Homebrew** for installing dependencies.

1. **Install Homebrew** (if not already installed):
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
   Verify installation:
   ```bash
   brew --version
   ```

2. **Install Dependencies**:
   Use Homebrew to install required tools:
   ```bash
   brew install python git wget tmux curl node npm yarn
   ```
   Verify installations:
   ```bash
   python3 --version
   node -v
   npm -v
   yarn -v
   ```

---

## **Step 2: Clone the RL Swarm Repository**
Clone the Gensyn RL Swarm repository from GitHub:
```bash
git clone https://github.com/gensyn-ai/rl-swarm.git
cd rl-swarm
```

---

## **Step 3: Set Up Python Virtual Environment**
Create and activate a Python virtual environment for the project:
```bash
python3 -m venv .venv
source .venv/bin/activate
```

---

## **Step 4: Install Python Dependencies**
Install the required Python packages using `pip`:
```bash
pip install -r requirements.txt
```

---

## **Step 5: Install Node.js Dependencies**
Navigate to the `modal-login` directory and install Node.js dependencies:
```bash
cd modal-login
yarn install
yarn upgrade && yarn add next@latest viem@latest
cd ..
```

---

## **Step 6: Run the RL Swarm Node**
Start the swarm node by running the script:
```bash
./run_rl_swarm.sh
```
Follow the prompts:
1. Confirm connection to the testnet (`Y`).
2. Open your browser and navigate to `http://localhost:3000/` if prompted.
3. Log in with your email and OTP.
4. Save your `ORG_ID` displayed in the terminal.

---

## **Step 7: Optional Configurations**
If you encounter memory issues on macOS, adjust PyTorch settings:

1. Open your shell configuration file:
   ```bash
   nano ~/.zshrc
   ```
2. Add these lines to the file:
   ```bash
   export PYTORCH_MPS_HIGH_WATERMARK_RATIO=0.0
   export PYTORCH_ENABLE_MPS_FALLBACK=1
   ```
3. Reload the configuration:
   ```bash
   source ~/.zshrc
   ```

---

## **Step 8: Monitor Logs**
Use `tmux` or `screen` to monitor logs in real-time:
```bash
tmux new -s gensyn-node
screen -S gensyn-node
```
To detach from a session, press `Ctrl+A` followed by `D`. Reattach using:
```bash
tmux attach -t gensyn-node
screen -r gensyn-node
```

---

## **Troubleshooting Common Issues**
- **wget not found**: Ensure `wget` is installed via Homebrew.
- **Memory errors**: Adjust PyTorch settings as described in Step 7.
- **Node stuck**: Modify GPU memory utilization settings in the configuration file (`~/rl-swarm/hivemind_exp/configs/mac/...`) as needed.

By following these steps, you should be able to successfully run the Gensyn RL Swarm node on your MacBook!
