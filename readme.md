## **Clean install Stable Diffusion on Windows with RTX 50xx Win 11**

***1. Prerequisites***
1.1 NVIDIA GeForce Driver - https://www.nvidia.com/en-us/drivers
1.2 Python 3.10.6 - https://www.python.org/downloads/release/python-3106/
1.3 GIT - https://git-scm.com/downloads/win
1.4 7-zip - https://www.7-zip.org/download.html


***2. Download Stable Diffusion for RTX 50xx GPU from GitHub***
2.1 Visit https://github.com/AUTOMATIC1111/stable-diffusion-webui/discussions/16818
2.2 Download sd.webui-1.10.1-blackwell.7z
2.3 Use 7-zip to extract the file to a new folder, e.g. C:\Apps\StableDiffusion\
2.4 Double click the 'update.bat' to update web UI to the latest version, wait till finish then close the window.
2.5 ***(Required for 50 Series GPUs)*** use the `switch-branch-toole.bat` to switch to `dev` branch.
2.6 Double click the `run.bat` to launch web UI, during the first launch it will download large amounts of files.
 After everything has been downloaded and installed correctly, you should see a message `"Running on local URL:  http://127.0.0.1:7860"`,
 opening the link will present you with the web UI interface.


***3. Download a model from Hugging Face***
3.1 Visit https://huggingface.co/stable-diffusion-v1-5/stable-diffusion-v1-5
3.2 Download `v1-5-pruned.safetensors`
3.3 Save to models directory, e.g. C:\Apps\StableDiffusion\webui\models\Stable-diffusion\
3.4 Do not change the extension name of the file (.safetensors)
3.5 For more models, visit: https://huggingface.co/models


***4. Run WebUI***
4.1 Run run.bat in your new StableDiffusion folder
4.2 Wait for the WebUI to launch after installing the dependencies
4.3 Select the model from the dropdown
4.4 Enter your prompt, e.g. a lady with two children on green pasture in Monet style
4.5 Press Generate button
4.6 To monitor the GPU usage, type in Windows cmd prompt: nvidia-smi -l


***5. Setup xformers (dev version only):***
5.1 Run windows cmd and go to the webui directory, e.g. cd c:\Apps\StableDiffusion\webui
5.2 Type to create a dev branch: git branch dev
5.3 Type: `git switch dev`
5.4 Type: `pip install xformers==0.0.30`
5.5 Add this line to beginning of `webui.bat:
set XFORMERS_PACKAGE=xformers==0.0.30`
5.6 In `webui-user.bat`, change the `COMMANDLINE_ARGS` to:
`set COMMANDLINE_ARGS=--force-enable-xformers --xformers`
5.7 Type to check the modified file status: `git status`
5.8 Type to commit the change to dev: `git add webui.bat`
5.9 Type: `git add webui-user.bat`
5.10 Run: `..\run.bat`
5.11 The WebUI page should show at the bottom: xformers: 0.0.30