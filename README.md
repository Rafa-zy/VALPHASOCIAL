# VALPHASOCIAL: Benchmark and Self-Reflective Chain-of-Thought Generation for Visual Social Commonsense Reasoning

Here are the detailed steps to run eval on our benchmark. We provide two examples for reference.
### Step 0 Installation & Setup Essential Keys
Installation.
```bash
cd VLMEvalKit
pip install -e .
```

Setup keys.
```bash
# for Qwen
export DASHSCOPE_API_KEYS=""
#for gpt
export OPENAI_API_KEY=""
```

### Step 1 Downloading Benchmark & Generating .tsv File
Downloading benchmark:
Please search XiaohanSong/test_data at Hugging Face and download the folder test_data.

Generating .tsv file:
Go to visual_social.py, find line 80 and 90, and fill in the paths of test_qtva.json and test_slices of our benchmark. 
```bash
json_file = "" # path for test_qtva.json  
image_folder = ""  # path for test_slices/
```
Then, run this script and you will get a .tsv file called visual_social_grouped.tsv.

### Step 2 Filling in Paths for visual_social_grouped.tsv
You need to write down the path of visual_social_grouped.tsv you just generated to several places in different files, as shown below.
```bash
# 1. vlmeval/dataset/__init__.py line 218:
data_file = ''
# 2. vlmeval/dataset/image_base.py line 146:
return load("")
# 3. vlmeval/dataset/image_vqa.py line 943 & 1452":
data_path = ''
```
### Step 3 Evaluation for Qwen and GPT4o
Use the following commands.
```bash
python run.py --data visual_social --model QwenVLPlus  —verbose
python run.py --data visual_social --model GPT4o  —verbose
```
