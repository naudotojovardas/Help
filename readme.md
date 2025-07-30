## 🌟 **Clean Install: Stable Diffusion on Windows 11 (RTX 50xx)**

> **Beginner-friendly guide** to installing **Stable Diffusion Web UI** for **NVIDIA RTX 50xx** GPUs on **Windows 11** — no programming skills needed.  
> Just follow each step carefully and you'll be generating images in no time!

---

### ✅ **Step 1: Install Required Software (Only Once)**

> These are essential tools Stable Diffusion depends on.

1.1 🔧 [**NVIDIA GeForce Driver**](https://www.nvidia.com/en-us/drivers)  
→ Make sure your graphics drivers are **fully updated**.  
(Use GeForce Experience if unsure)

1.2 🐍 [**Python 3.10.6**](https://www.python.org/downloads/release/python-3106/)  
→ ⚠️ **Do not install Python 3.11 or later**, or the WebUI may not work.  
✅ During setup, **check the box that says "Add Python to PATH"**.

1.3 🌳 [**GIT for Windows**](https://git-scm.com/downloads/win)  
→ Git lets your system download and manage project files from GitHub.

1.4 📦 [**7-Zip**](https://www.7-zip.org/download.html)  
→ This tool is used to extract `.7z` archive files.

---

### 📥 **Step 2: Download Stable Diffusion Web UI (RTX 50xx build)**

> A customized version optimized for your RTX 50-series GPU.

2.1 🌐 Visit: [AUTOMATIC1111 RTX 50xx build discussion](https://github.com/AUTOMATIC1111/stable-diffusion-webui/discussions/16818)  
2.2 ⬇️ Download the file: `sd.webui-1.10.1-blackwell.7z`  
2.3 📁 Extract it using 7-Zip to a folder, e.g. `C:\Apps\StableDiffusion\`  
2.4 🛠️ Double-click `update.bat`  
→ This will update the Web UI to the latest files. Let it finish.

2.5 ⚠️ **Important for RTX 50xx users:**  
→ Run `switch-branch-toole.bat` and select the `dev` branch

2.6 🚀 Double-click `run.bat`  
→ This will launch the UI and install everything needed (this can take 5–15 minutes).  
You’ll see:  
```
Running on local URL: http://127.0.0.1:7860
```
Click or paste that into your browser to access the **Web UI**!

---

### 🧠 **Step 3: Add a Model (Required to Generate Images)**

> Models are like "brains" that let Stable Diffusion understand and generate images.

3.1 🌐 Visit: [Hugging Face - stable-diffusion-v1-5](https://huggingface.co/stable-diffusion-v1-5/stable-diffusion-v1-5)  
3.2 ⬇️ Download: `v1-5-pruned.safetensors`  
3.3 🗂️ Save it to:  
```plaintext
e.g. C:\Apps\StableDiffusion\webui\models\Stable-diffusion\
```

3.4 ⚠️ **Do not rename the file extension** — it must end in `.safetensors`  
3.5 For more models, check: [HuggingFace.co/models](https://huggingface.co/models)

---

### 🖼️ **Step 4: Use the Web UI**

> Let’s generate your first image!

4.1 ▶️ Double-click `run.bat`  
4.2 ⏳ Wait for WebUI to load — it will install more dependencies if needed  
4.3 🧠 In the UI, select your downloaded model (e.g., `v1-5-pruned.safetensors`)  
4.4 📝 In the prompt box, type something like:  
```
A lady with two children on a green pasture in Monet style
```

4.5 🔘 Click "Generate"  
4.6 📊 (Optional) To monitor GPU usage, run this in CMD:  
```
nvidia-smi -l
```

---

### ⚙️ **Step 5: Enable Xformers (Optional — For Dev Branch)**

> This improves performance but is only available in the `dev` branch (which you already switched to in Step 2.5).

5.1 🪟 Open **Command Prompt**  
5.2 📁 Go to your WebUI folder:  
```bash
e.g. cd C:\Apps\StableDiffusion\webui
```

5.3 🛠️ Create the `dev` branch:
```bash
git branch dev
git switch dev
```

5.4 📦 Install xformers:
```bash
pip install xformers==0.0.30
```

5.5 📝 Open `webui.bat`, add this **at the top**:
```bash
set XFORMERS_PACKAGE=xformers==0.0.30
```

5.6 📝 In `webui-user.bat`, change the line:
```bash
set COMMANDLINE_ARGS=--force-enable-xformers --xformers
```

5.7 ✅ Check status:
```bash
git status
```

5.8 💾 Save and commit changes:
```bash
git add webui.bat
git add webui-user.bat
```

5.9 ▶️ Run WebUI again:
```bash
..\run.bat
```

5.10 ✅ You should see at the bottom of the WebUI page:
```
xformers: 0.0.30
```

---

### 🧩 **Next Steps (Optional)**

- Try downloading different models and styles from HuggingFace
- Experiment with different prompts, negative prompts, and settings
- Use extensions or ControlNet for advanced features
