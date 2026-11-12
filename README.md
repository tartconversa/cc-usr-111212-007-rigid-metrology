# 固定标志点的刚体配准与退化诊断

本项目保存虚构台架测量表及Python读取工具。当前工具加载文件并检查输入，不执行统计检验、求解、配准或分析。所有仪器、试件、对象与人工标签均为合成。

## 字段与单位

x/y坐标是静态同键点，unit为mm，weight是正标量，split预定fit/check，group是独立标定组；不存在时间轴或连续路径。

material-index.json记录全部输入内容哈希；fixtures保存原始资料与配置，计算输出可放.workspace-output，原始资料不应被覆盖。

## 运行已有读取器

Python 3.11以上，标准库即可，不需安装第三方依赖。

    python -m src.metrology_reader fixtures/points.csv
    python -m compileall -q src tests
    python -m unittest discover -s tests -v

## 固定容器

    docker build -t rigid-metrology:local .
    docker run --rm rigid-metrology:local

容器镜像以完整digest固定，默认仅检查输入契约；实现新增分析功能所需依赖由开发者明确登记。
