---
{"dg-publish":true,"permalink":"/05 - 计算机，AI/chatgpt/txt转md，by chatgpt/","created":"2024-06-12T00:01:55.090+08:00","updated":"2024-06-12T12:53:42.756+08:00","dg-note-properties":{}}
---


背景：为了导入一些 TXT 文档进 Obsidian，搜了下脚本没搜到，看到有人发了类似的专栏，但是是图片格式，于是参考他的方法，用 ChatGpt 整了这个 txt 转 markdown 脚本，全程如下：

# 我 ：

你好我想批量转换TXT文档为Markdown文档，请问能写个Python脚本教教我吗

# ChatGPT : 

当然可以！下面是一个简单的Python脚本，用于将TXT文档批量转换为Markdown文档。假设你的TXT文档位于一个文件夹中，这个脚本会读取该文件夹中的所有TXT文件，并将其内容转换为Markdown格式后，保存为同名的Markdown文件。

首先，确保你已经安装了Python。如果没有，可以从[Python官方网站](https://www.python.org/)下载并安装。

然后，创建一个Python脚本文件，例如`txt_to_md.py`，并将以下代码粘贴到该文件中：

```
import os

def convert_txt_to_md(input_dir, output_dir):
    # 确保输出目录存在
    if not os.path.exists(output_dir):
        os.makedirs(output_dir)

    # 遍历输入目录中的所有文件
    for filename in os.listdir(input_dir):
        if filename.endswith('.txt'):
            # 构建完整的文件路径
            txt_file_path = os.path.join(input_dir, filename)
            md_file_path = os.path.join(output_dir, filename.replace('.txt', '.md'))

            # 读取TXT文件内容
            with open(txt_file_path, 'r', encoding='utf-8') as txt_file:
                content = txt_file.read()

            # 将内容写入Markdown文件
            with open(md_file_path, 'w', encoding='utf-8') as md_file:
                md_file.write(content)

            print(f'Converted {txt_file_path} to {md_file_path}')

if __name__ == "__main__":
    input_directory = 'path/to/your/txt/files'  # 替换为你的TXT文件夹路径
    output_directory = 'path/to/save/md/files'  # 替换为你想要保存Markdown文件的文件夹路径

    convert_txt_to_md(input_directory, output_directory)

```

### 步骤说明：

1. **导入所需模块**：
    
    - `os`模块用于处理文件和目录。
2. **定义`convert_txt_to_md`函数**：
    
    - 该函数接收两个参数：`input_dir`和`output_dir`，分别表示输入和输出目录。
    - 如果输出目录不存在，使用`os.makedirs`创建它。
    - 使用`os.listdir`获取输入目录中的所有文件，遍历这些文件。
    - 检查文件扩展名是否为`.txt`，如果是，则读取文件内容，并将其写入同名的Markdown文件（扩展名改为`.md`）。
3. **主程序**：
    
    - 设置输入和输出目录的路径。
    - 调用`convert_txt_to_md`函数，开始转换。

### 使用方法：

1. 将上述脚本保存为`txt_to_md.py`。
2. 在脚本中替换`input_directory`和`output_directory`为你的TXT文件夹路径和Markdown文件夹路径。
3. 打开终端（或命令提示符），导航到脚本所在的目录。
4. 运行脚本：
```
python txt_to_md.py
```

这样，脚本会读取指定目录中的所有TXT文件，并将其内容保存为同名的Markdown文件到指定的输出目录中。

# 我 ：

UnicodeDecodeError: 'utf-8' codec can't decode byte 0xbb in position 0: invalid start byte

# ChatGPT:

这个错误通常是由于文件的编码不是UTF-8导致的。TXT文件可能使用了其他编码方式（例如GBK、ISO-8859-1等）。我们可以尝试自动检测文件的编码，并根据检测结果进行读取。

为了实现这一点，我们可以使用 `chardet` 库来检测文件的编码。首先，你需要安装这个库：

```
pip install chardet
```

然后，修改脚本如下：

```
import os
import chardet

def detect_encoding(file_path):
    with open(file_path, 'rb') as f:
        raw_data = f.read()
    result = chardet.detect(raw_data)
    encoding = result['encoding']
    return encoding

def convert_txt_to_md(input_dir, output_dir):
    # 确保输出目录存在
    if not os.path.exists(output_dir):
        os.makedirs(output_dir)

    # 遍历输入目录中的所有文件
    for filename in os.listdir(input_dir):
        if filename.endswith('.txt'):
            # 构建完整的文件路径
            txt_file_path = os.path.join(input_dir, filename)
            md_file_path = os.path.join(output_dir, filename.replace('.txt', '.md'))

            # 检测文件编码
            encoding = detect_encoding(txt_file_path)
            if encoding is None:
                print(f"Could not detect encoding for {txt_file_path}. Skipping file.")
                continue

            # 读取TXT文件内容
            try:
                with open(txt_file_path, 'r', encoding=encoding) as txt_file:
                    content = txt_file.read()

                # 将内容写入Markdown文件
                with open(md_file_path, 'w', encoding='utf-8') as md_file:
                    md_file.write(content)

                print(f'Converted {txt_file_path} to {md_file_path}')
            except Exception as e:
                print(f"Error reading or writing file {txt_file_path}: {e}")

if __name__ == "__main__":
    input_directory = 'path/to/your/txt/files'  # 替换为你的TXT文件夹路径
    output_directory = 'path/to/save/md/files'  # 替换为你想要保存Markdown文件的文件夹路径

    convert_txt_to_md(input_directory, output_directory)

```

### 修改说明：

1. **导入 `chardet` 库**：用于检测文件编码。
    
2. **定义 `detect_encoding` 函数**：
    
    - 读取文件的二进制内容并使用 `chardet.detect` 来检测编码。
3. **在 `convert_txt_to_md` 函数中**：
    
    - 调用 `detect_encoding` 函数来检测每个TXT文件的编码。
    - 使用检测到的编码读取TXT文件内容。
    - 将内容写入Markdown文件时，仍然使用UTF-8编码。
4. **异常处理**：
    
    - 在读取和写入文件时添加异常处理，以便在发生错误时输出错误信息并跳过该文件。

### 使用方法：

1. 安装 `chardet` 库：
```
pip install chardet
```

2. 将脚本保存为 `txt_to_md.py`。
3. 在脚本中替换 `input_directory` 和 `output_directory` 为你的TXT文件夹路径和Markdown文件夹路径。
4. 打开终端（或命令提示符），导航到脚本所在的目录。
5. 运行脚本：
```
python txt_to_md.py
```


这样，脚本会自动检测每个TXT文件的编码，并正确地读取和转换它们的内容。

# 我 ：

能添加深度遍历吗，至少三层

# ChatGPT:

当然可以，我们可以在原有脚本的基础上添加递归遍历功能，支持至少三层的目录深度遍历。以下是修改后的脚本：

```
import os
import chardet

def detect_encoding(file_path):
    with open(file_path, 'rb') as f:
        raw_data = f.read()
    result = chardet.detect(raw_data)
    encoding = result['encoding']
    return encoding

def convert_txt_to_md(input_dir, output_dir):
    # 遍历输入目录中的所有文件和子目录
    for root, dirs, files in os.walk(input_dir):
        # 创建对应的输出目录结构
        relative_path = os.path.relpath(root, input_dir)
        target_dir = os.path.join(output_dir, relative_path)
        if not os.path.exists(target_dir):
            os.makedirs(target_dir)

        for filename in files:
            if filename.endswith('.txt'):
                # 构建完整的文件路径
                txt_file_path = os.path.join(root, filename)
                md_file_path = os.path.join(target_dir, filename.replace('.txt', '.md'))

                # 检测文件编码
                encoding = detect_encoding(txt_file_path)
                if encoding is None:
                    print(f"Could not detect encoding for {txt_file_path}. Skipping file.")
                    continue

                # 读取TXT文件内容
                try:
                    with open(txt_file_path, 'r', encoding=encoding) as txt_file:
                        content = txt_file.read()

                    # 将内容写入Markdown文件
                    with open(md_file_path, 'w', encoding='utf-8') as md_file:
                        md_file.write(content)

                    print(f'Converted {txt_file_path} to {md_file_path}')
                except Exception as e:
                    print(f"Error reading or writing file {txt_file_path}: {e}")

if __name__ == "__main__":
    input_directory = 'path/to/your/txt/files'  # 替换为你的TXT文件夹路径
    output_directory = 'path/to/save/md/files'  # 替换为你想要保存Markdown文件的文件夹路径

    convert_txt_to_md(input_directory, output_directory)

```

### 修改说明：

1. **使用 `os.walk` 遍历目录结构**：
    
    - `os.walk` 会递归遍历目录结构，返回每一个根目录、子目录和文件列表。
    - 对于每个根目录，创建对应的输出目录结构。
2. **处理每个文件**：
    
    - 对于每个文件，检测编码，读取内容，并写入Markdown文件。

### 使用方法：

1. 安装 `chardet` 库（如果还没有安装）：
```
pip install chardet
```

2. 将脚本保存为 `txt_to_md.py`。
3. 在脚本中替换 `input_directory` 和 `output_directory` 为你的TXT文件夹路径和Markdown文件夹路径。
4. 打开终端（或命令提示符），导航到脚本所在的目录。
5. 运行脚本：
```
python txt_to_md.py
```

这样，脚本会递归遍历指定的输入目录及其子目录，并将所有TXT文件转换为Markdown文件，保存在对应的输出目录结构中。

---

# End

经测试，完美~

...

了吗？

还能更好！

经过观察，我要处理的这些文档有个共同点，相当一部分是用汉字的一，二，三为分段标题。

并且我希望每个 TXT 文档开头能添加一个数字花园插件（DigitalGarden）发布的属性：

```
---

dg-publish: true

---
```

于是：

 
 ```
import os
import chardet

# 定义汉字数字替换映射
chinese_to_md_number = {
    "一": "# 一",
    "二": "# 二",
    "三": "# 三",
    "四": "# 四",
    "五": "# 五",
    "六": "# 六",
    "七": "# 七",
    "八": "# 八",
    "九": "# 九",
    "十": "# 十"
}

def detect_encoding(file_path):
    with open(file_path, 'rb') as f:
        raw_data = f.read()
    result = chardet.detect(raw_data)
    encoding = result['encoding']
    return encoding

def process_content(content):
    # 将每个换行符替换为换行
    lines = content.splitlines()
    processed_lines = []
    empty_line = False

    for line in lines:
        # 检查段落前面的四个空格并替换成换行
        if line.startswith("    "):
            line = line.replace("    ", "\n", 1)

        # 如果是一个汉字数字为一行
        if line.strip() != "":
            if len(line.strip()) == 1 and line.strip() in chinese_to_md_number:
                line = chinese_to_md_number[line.strip()]  # 替换汉字数字

        processed_lines.append(line)

    processed_content = "\n".join(processed_lines)
    return processed_content

def convert_txt_to_md(input_dir, output_dir):
    for root, dirs, files in os.walk(input_dir):
        relative_path = os.path.relpath(root, input_dir)
        target_dir = os.path.join(output_dir, relative_path)
        if not os.path.exists(target_dir):
            os.makedirs(target_dir)

        for filename in files:
            if filename.endswith('.txt'):
                txt_file_path = os.path.join(root, filename)
                md_file_path = os.path.join(target_dir, filename.replace('.txt', '.md'))

                encoding = detect_encoding(txt_file_path)
                if encoding is None:
                    print(f"Could not detect encoding for {txt_file_path}. Skipping file.")
                    continue

                try:
                    with open(txt_file_path, 'r', encoding=encoding) as txt_file:
                        content = txt_file.read()

                    processed_content = process_content(content)

                    # 在文件内容之前添加头部信息
                    markdown_content = "---\ndg-publish:\n---\n\n" + processed_content

                    with open(md_file_path, 'w', encoding='utf-8') as md_file:
                        md_file.write(markdown_content)

                    print(f'Converted {txt_file_path} to {md_file_path}')
                except Exception as e:
                    print(f"Error reading or writing file {txt_file_path}: {e}")

if __name__ == "__main__":
    input_directory = 'D:/输入文件夹'  # 替换为您的TXT文件夹路径
    output_directory = 'D:/输出文件夹'  # 替换为您的Markdown文件输出路径

    convert_txt_to_md(input_directory, output_directory)>)
```

这下应该真正结束了...

