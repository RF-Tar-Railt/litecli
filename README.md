# Cli-Lite

一个简单的框架，用于构建 CLI 工具。基于 [`Alconna`](https://github.com/ArcletProject/Alconna)

[English Version](README_ENG.md)


## 安装

```shell
pip install cli-lite
```

## 示例

编写示例代码如下：

```python
# example.py
from clilte import BasePlugin, CommandLine, PluginMetadata
from arclet.alconna import Alconna, Arparma, Args, CommandMeta, Option


class MyPlugin(BasePlugin):

    def init(self) -> Alconna | str:
        return Alconna("hello", Args["name", str], meta=CommandMeta("测试命令"))

    def meta(self) -> PluginMetadata:
        return PluginMetadata("hello", "0.0.1", "我的第一个插件", ["dev"], ["john"])

    def dispatch(self, result: Arparma) -> bool | None:
        return print(f"Hello! {result.name}")

    @classmethod
    def supply_options(cls) -> list[Option] | None:
        return 


if __name__ == '__main__':
    cli = CommandLine(title="我的第一个 CLI", version="示例 0.0.1")
    cli.add(MyPlugin)
    cli.main()
```

然后执行以下命令：

```shell
python example.py hello world
```

你将得到以下结果：

```shell
Hello! world
```