# 仪器测量与校准记录

本项目使用 Python 3.11 及以上版本，仅依赖标准库，无需安装第三方包。数据文件均为本地合成记录，不含真实个人或机构资料。

metrology/ingress 校验导入；calibration 管理单位与证书，支持正斜率线性修正拟合；ledger 保存观测和审计；processing 运行窗口与活动；output 保存快照和导出包。

证书使用有效期和仪器通道选择，原读数、校正值和证书身份分别保存。现有拟合从仪器示值预测参考值，不自动生成或替换证书。所有单位换算需经过单位注册表。

在项目根目录运行完整测试：

```sh
python3 -m unittest discover -s tests -v
```

编译检查：

```sh
python3 -m compileall -q .
```

实际演示：

```sh
python3 -m metrology demo
```

演示在临时目录内建立本地状态，结束后自动清理。测试、编译与演示在依赖已准备的环境内均不下载数据或软件。输入错误以非零退出码及错误对象报告。更多子命令可通过对应入口的 --help 查看。

容器环境可执行 `docker build -t local-analysis .`，再运行 `docker run --rm --network none local-analysis`。镜像固定基础内容摘要，构建后运行只访问本地文件。完整测试与演示也可直接使用已有 Python 环境。
