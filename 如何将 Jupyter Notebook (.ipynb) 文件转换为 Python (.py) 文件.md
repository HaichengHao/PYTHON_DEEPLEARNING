 

### 前言

在这篇文章中，我将向大家介绍如何将 Jupyter Notebook (.[ipynb](https://so.csdn.net/so/search?q=ipynb&spm=1001.2101.3001.7020)) 文件转换为 Python (.py) 文件。这篇文章将包含一些代码示例，帮助你更轻松地理解这个过程。

### 为什么要进行转换？

在某些情况下，你可能需要将 Jupyter Notebook 文件转换为 Python 文件，例如：

*   为了在生产环境中运行代码；
*   与其他开发人员分享代码时，他们可能更熟悉 Python 文件；
*   或者你只是想在纯文本编辑器中编辑代码。

在这里我会分享三种方法进行转转。

### 方法 1：使用 Jupyter Notebook

如果你已经安装了 Jupyter Notebook，那么你可以使用 Jupyter Notebook 自带的功能将 .ipynb 文件转换为 .py 文件。以下是操作步骤：

1.  打开你的 Jupyter Notebook 文件；
2.  点击菜单栏的 File > Download as > Python (.py)；
3.  文件将会自动下载为 .py 文件。  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d5a49b25bafaf2dee9dea856b6258e51.png)

### 方法 2：使用命令行

你还可以使用命令行工具 jupyter nbconvert 将 .ipynb 文件转换为 .py 文件。首先，请确保你已经安装了 Jupyter：

```python
pip install jupyter
```

然后，运行以下命令将你的 .ipynb 文件转换为 .py 文件——记得进入到你所在的.ipynb 文件目录下：

```python
jupyter nbconvert --to script your_notebook.ipynb
```

将 your\_notebook.ipynb 替换为你的 Jupyter Notebook 文件名。转换后的 .py 文件将与 .ipynb 文件位于同一目录。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/7156ef4f8b129af3669a43c2c20da333.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/68ab404330aed0a258b677d35deef229.png)  
这时在目录下就会生成对应的.py文件。

### 方法 3：使用 Python 脚本

最后，你还可以使用 Python 脚本将 .ipynb 文件转换为 .py 文件。这里是一个简单的 Python 脚本，用于完成这个任务：

```python
import json

def convert_ipynb_to_py(ipynb_file, py_file):
    with open(ipynb_file, 'r',encoding='utf-8') as f:
        notebook = json.load(f)

    with open(py_file, 'w',encoding='utf-8') as f:
        for cell in notebook['cells']:
            if cell['cell_type'] == 'code':
                f.write(''.join(cell['source']) + '\n\n')
```

要使用这个脚本，你只需要调用 convert\_ipynb\_to\_py 函数，并传入 .ipynb 文件和期望的 .py 文件名：

```python
convert_ipynb_to_py('your_notebook.ipynb', 'your_notebook.py')
```

将 ‘your\_notebook.ipynb’ 和 ‘your\_notebook.py’ 替换为你的文件名。

### 结论

在本文中，我向大家展示了三种将 Jupyter Notebook 文件转换为 Python 文件的方法。现在，你应该能够根据你的需求和喜好选择合适的方法。如果你觉得这篇文章对你有帮助，一键三连。感谢阅读！

本文转自 <https://blog.csdn.net/qq_69218005/article/details/131339237>，如有侵权，请联系删除。