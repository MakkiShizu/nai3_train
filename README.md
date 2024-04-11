# ✨ nai3_train ✨

英文版说明：[English Documentation](./README_EN.md)

如果你需要使用nai3生成的图片来批量训练你的SD模型，那我想你需要这个项目。

nai3生成的图片，一键生成、打标和处理脚本

原理1：从prompt_folder随机抽取txt作为prompt批量生成随机素材

把你的打标txt变成你的随机提示词库！

原理2：从json中随机抽取角色生成随机角色，或者按顺序生成所有角色

备注：欢迎提出新功能，脚本还在不断优化中

## 💿 安装运行环境

```bash
pip install pdm
# 自动创建虚拟环境并锁定依赖版本
pdm install
```

## ⚙️ 配置

> 使用记事本等文本编辑器打开本目录下 `.env` 文件, 根据注释进行个性化配置, 其中 **token** 是必需的, 其它均可以保持默认

token 获取方法:

- 在网页（https://novelai.net） 中登录你的 NovelAI 账号
- 在左上角个人中心中找到 “Account”
- 找到 “Get Persistent API Token.” 栏目
- 点击 “Generate Token” 按钮生成 token

### ⚠️一些常见的报错：

random_characetrs.py保存第一个图像时报错：小bug，保存第一个时必定失败，后面就正常了

## ✨ 支持的所有采样器列表

```
            "k_euler",
            "k_euler_ancestral",
            "k_dpmpp_2s_ancestral",
            "k_dpmpp_2m",
            "k_dpmpp_sde",
            "ddim_v3",
```

## ✨ 生成的随机角色效果：

图一

![VA}S0W4AL6_ZIV~2 (BDX5](https://github.com/wochenlong/nai3_train/assets/117965575/6bfecd63-fa7f-4b36-bef9-1e8df2eef21f)

图二

![0~O)3% YX{SRSL$2VY)PTJ](https://github.com/wochenlong/nai3_train/assets/117965575/093c08fc-bf83-4d38-a282-7470bf48e316)

图三：

![L_ZUGFLNWQXDY~4(A4~5XK2](https://github.com/wochenlong/nai3_train/assets/117965575/711aff18-3ef7-4390-889e-c0ffc846418e)

图四：
![V2L6B62X60RU7((XCBMAN 9](https://github.com/wochenlong/nai3_train/assets/117965575/7b290ae4-5d77-4210-9276-519bd8afe6d6)

## ✨ 生成的随机素材效果：

图四：
![8R@KZV(13`(0U~25~KKQTR7](https://github.com/wochenlong/nai3_train/assets/117965575/1c5a42bf-b44e-48a6-aaab-aa5487554a42)

图五：
![N9 KXF41KXXB2T~CKZ2VS`M](https://github.com/wochenlong/nai3_train/assets/117965575/37e1801f-bfea-4f7c-8701-ed4047c29a28)

## 🤗 开源随机提示词库

海量txt随机提示词，解压后放进`prompt_folder`即可。

一、 4K高质量提示词库 ：https://huggingface.co/datasets/windsingai/random_prompt/resolve/main/prompt_4k.zip

特点：人工整理，良品率高，安全性高，只有2%的nsfw

内容：以人物和构图为主

来源：修改自尤吉的AID训练集的打标文件

二、 20w高质量提示词库 ：https://huggingface.co/datasets/windsingai/random_prompt/resolve/main/prompt_20W.zip

特点：真实图片反推，数量多，二次元浓度高，足够泛化，约有20%的nsfw

内容：题材很多，考虑到danbooru的构成，主要还是以女性为主

来源：从 https://danbooru.donmai.us/ 批量爬取，修改自杠杠哥的20W训练集

## 🎉 快速上手

### 1️⃣ random_characetrs.py

随机/按顺序生成指定角色的图片

原理，从json读取角色名，生成图片

本仓库内置包括原神、明日方舟、fgo等多个主流游戏的随机角色库。

例：
使用通过读取.\json\genshin.json 文件，实现随机原神角色生成。

json文件的结构，以genshin.json为例：

```
{
  "role": [
    "noelle_(genshin_impact)",
    "faruzan_(genshin_impact)",
    "角色1",
    "角色2",
    "角色3",
    .....
  ]
```

### 2️⃣ random_prompt.py

读取随机提示词库，批量生成随机nai3图片

### 3️⃣ nai3tagger.py

读取图片信息，并生成txt同名文件

### 4️⃣ clear.py

去掉txt文件中的前缀`prefix` ，绑定画风

### 5️⃣ UTF-8.py

去掉txt文件中的非法字符，比如😄🙃

txt文件中的部分非法字符，可能会令训练发生报错，训练脚本无法读取txt，因此，去掉非法字符是必需的

### 6️⃣ cut.py

去掉图片中的水印 （测试功能）


