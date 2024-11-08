# ✨ nai3_train ✨

Chinese Version: [中文版本](./README.md)

If you need to use images generated by nai3 for bulk training of your SD model, this project is for you.

nai3 generates images, and this project provides a one-click script for generating, tagging, and processing these images.

Principle 1: Randomly extract text from the `prompt_folder` directory as a prompt to generate random materials in bulk.

Turn your tagged txt into your random prompt library!

Principle 2: Randomly extract characters from json to generate random characters, or generate all characters in order.

Note: New features are welcome, and the script is continuously being optimized.

## 💿 Installation and Running Environment

```bash
pip install pdm
# Automatically create a virtual environment and lock dependency versions
pdm install
```

## ⚙️ Configuration

> Use a text editor such as Notepad to open the `config.toml` file in this directory, and configure it according to the comments. The **token** is required, and the rest can be left as default.

How to get the token:

- Log in to your NovelAI account on the webpage ([https://novelai.net](https://novelai.net))
- Find "Account" in the top left personal center
- Find the "Get Persistent API Token." section
- Click the "Generate Token" button to generate a token

## ✨ Supported Samplers

```
"k_euler",
"k_euler_ancestral",
"k_dpmpp_2s_ancestral",
"k_dpmpp_2m",
"k_dpmpp_sde",
"ddim_v3",
```

## ✨ Generated Random Character Effects:

Image 1

![Image1](https://github.com/wochenlong/nai3_train/assets/117965575/6bfecd63-fa7f-4b36-bef9-1e8df2eef21f)

Image 2

![Image2](https://github.com/wochenlong/nai3_train/assets/117965575/093c08fc-bf83-4d38-a282-7470bf48e316)

Image 3:

![Image3](https://github.com/wochenlong/nai3_train/assets/117965575/711aff18-3ef7-4390-889e-c0ffc846418e)

Image 4:

![Image4](https://github.com/wochenlong/nai3_train/assets/117965575/7b290ae4-5d77-4210-9276-519bd8afe6d6)

## ✨ Generated Random Material Effects:

Image 4:

![Image4](https://github.com/wochenlong/nai3_train/assets/117965575/1c5a42bf-b44e-48a6-aaab-aa5487554a42)

Image 5:

![Image5](https://github.com/wochenlong/nai3_train/assets/117965575/37e1801f-bfea-4f7c-8701-ed4047c29a28)

## 🤗 Open Source Random Prompt Library

A massive txt random prompt library, just unzip and put it into `prompt_folder`.

| Library  | 4K High Quality                                                                                        | 200K High Quality                                                                                                        |
|----------|--------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| Features | Manually sorted, high quality rate, high safety, only 2% nsfw                                          | Real image reverse push, large quantity, high concentration of secondary elements, enough generalization, about 20% nsfw |
| Content  | Mainly characters and composition                                                                      | Many themes, considering the composition of danbooru, mainly female characters                                           |
| Source   | Modified from Yoshiji's AID training set tagging file                                                  | Bulk crawled from [https://danbooru.donmai.us/](https://danbooru.donmai.us/), modified from Brother Ganggang's 200K training set                        |
| Download | [4K High Quality](https://huggingface.co/datasets/windsingai/random_prompt/resolve/main/prompt_4k.zip) | [200K High Quality](https://huggingface.co/datasets/windsingai/random_prompt/resolve/main/prompt_20W.zip)                |

## 🎉 Quick Start

### 1️⃣ random_characetrs.py

Generate specified characters' images randomly or in order.

Principle: Read character names from json and generate images.

This repository includes random character libraries of several mainstream games including Genshin Impact, Arknights, FGO, etc.

Example:
Use by reading the .\json\genshin.json file to generate random Genshin Impact characters.

The structure of the json file, taking genshin.json as an example:

```
{
  "role": [
    "noelle_(genshin_impact)",
    "faruzan_(genshin_impact)",
    "Character 1",
    "Character 2",
    "Character 3",
    .....
  ]
}
```

### 2️⃣ random_prompt.py

Read the random prompt library and generate random nai3 images in bulk.

### 3️⃣ nai3tagger.py

Read image information and generate a txt file with the same name.

### 4️⃣ clear.py

Remove the prefix `prefix` from the txt file to bind the style.

### 5️⃣ UTF-8.py

Remove illegal characters from the txt file, such as 😄🙃.

Some illegal characters in the txt file may cause errors during training, and the training script cannot read the txt, so removing illegal characters is necessary.

### 6️⃣ cut.py

Remove the watermark from the image (test feature).