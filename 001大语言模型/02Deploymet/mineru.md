## mineru

[opendatalab/MinerU: A high-quality tool for convert PDF to Markdown and JSON.一站式开源高质量数据提取工具，将PDF转换成Markdown和JSON格式。](https://github.com/opendatalab/MinerU?tab=readme-ov-file#using-mps)

[Install — MinerU 1.3.11 documentation](https://mineru.readthedocs.io/en/latest/user_guide/install/install.html)

magic-pdf -p /Users/Daglas/Downloads/test.pdf -o /Users/Daglas/Downloads

### 安装

#### Create an environment

conda create -n mineru 'python=3.12' -y
conda activate mineru
pip install -U "magic-pdf[full]"

#### Download model weight files

pip install huggingface_hub

wget https://github.com/opendatalab/MinerU/raw/master/scripts/download_models_hf.py -O download_models_hf.py

python3.12 download_models_hf.py

#### Install LibreOffice[Optional]

This section is required for handle doc, docx, ppt, pptx filetype, You can skip this section if no need for those filetype processing.

Linux/Macos Platform

apt-get/yum/brew install libreoffice

brew install libreoffice

#### 加速

Using MPS
If your device uses Apple silicon chips, you can enable MPS acceleration for your tasks.

You can enable MPS acceleration by setting the device-mode parameter to mps in the magic-pdf.json configuration file.

{
    // other config
    "device-mode": "mps"
}


magic-pdf --help
Usage: magic-pdf [OPTIONS]

Options:
  -v, --version                display the version and exit
  -p, --path PATH              local filepath or directory. support PDF, PPT,
                               PPTX, DOC, DOCX, PNG, JPG files  [required]
  -o, --output-dir PATH        output local directory  [required]
  -m, --method [ocr|txt|auto]  the method for parsing pdf. ocr: using ocr
                               technique to extract information from pdf. txt:
                               suitable for the text-based pdf only and
                               outperform ocr. auto: automatically choose the
                               best method for parsing pdf from ocr and txt.
                               without method specified, auto will be used by
                               default.
  -l, --lang TEXT              Input the languages in the pdf (if known) to
                               improve OCR accuracy.  Optional. You should
                               input "Abbreviation" with language form url: ht
                               tps://paddlepaddle.github.io/PaddleOCR/en/ppocr
                               /blog/multi_languages.html#5-support-languages-
                               and-abbreviations
  -d, --debug BOOLEAN          Enables detailed debugging information during
                               the execution of the CLI commands.
  -s, --start INTEGER          The starting page for PDF parsing, beginning
                               from 0.
  -e, --end INTEGER            The ending page for PDF parsing, beginning from
                               0.
  --help                       Show this message and exit.


\## show version
magic-pdf -v

\## command line example
magic-pdf -p {some_pdf} -o {some_output_dir} -m auto


### 其他

配置文件的路径：

/Users/Daglas/magic-pdf.json

下载模型的路径：


layoutreader_model_dir is: /Users/Daglas/.cache/huggingface/hub/models--hantian--layoutreader/snapshots/641226775a0878b1014a96ad01b9642915136853

The configuration file has been configured successfully, the path is: /Users/Daglas/magic-pdf.json


download_models_hf.py
```py
import json
import os
import shutil

import requests
from huggingface_hub import snapshot_download


def download_json(url):
    # 下载JSON文件
    response = requests.get(url)
    response.raise_for_status()  # 检查请求是否成功
    return response.json()


def download_and_modify_json(url, local_filename, modifications):
    if os.path.exists(local_filename):
        data = json.load(open(local_filename))
        config_version = data.get('config_version', '0.0.0')
        if config_version < '1.2.0':
            data = download_json(url)
    else:
        data = download_json(url)

    # 修改内容
    for key, value in modifications.items():
        data[key] = value

    # 保存修改后的内容
    with open(local_filename, 'w', encoding='utf-8') as f:
        json.dump(data, f, ensure_ascii=False, indent=4)


if __name__ == '__main__':

    mineru_patterns = [
        # "models/Layout/LayoutLMv3/*",
        "models/Layout/YOLO/*",
        "models/MFD/YOLO/*",
        "models/MFR/unimernet_hf_small_2503/*",
        "models/OCR/paddleocr_torch/*",
        # "models/TabRec/TableMaster/*",
        # "models/TabRec/StructEqTable/*",
    ]
    model_dir = snapshot_download('opendatalab/PDF-Extract-Kit-1.0', allow_patterns=mineru_patterns)

    layoutreader_pattern = [
        "*.json",
        "*.safetensors",
    ]
    layoutreader_model_dir = snapshot_download('hantian/layoutreader', allow_patterns=layoutreader_pattern)

    model_dir = model_dir + '/models'
    print(f'model_dir is: {model_dir}')
    print(f'layoutreader_model_dir is: {layoutreader_model_dir}')

    # paddleocr_model_dir = model_dir + '/OCR/paddleocr'
    # user_paddleocr_dir = os.path.expanduser('~/.paddleocr')
    # if os.path.exists(user_paddleocr_dir):
    #     shutil.rmtree(user_paddleocr_dir)
    # shutil.copytree(paddleocr_model_dir, user_paddleocr_dir)

    json_url = 'https://github.com/opendatalab/MinerU/raw/master/magic-pdf.template.json'
    config_file_name = 'magic-pdf.json'
    home_dir = os.path.expanduser('~')
    config_file = os.path.join(home_dir, config_file_name)

    json_mods = {
        'models-dir': model_dir,
        'layoutreader-model-dir': layoutreader_model_dir,
    }

    download_and_modify_json(json_url, config_file, json_mods)
    print(f'The configuration file has been configured successfully, the path is: {config_file}')

```