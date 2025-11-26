# RangerMorph
├── src/
│   └── rangermorph/
│       ├── __init__.py
│       ├── cli/                 # 命令行入口与子命令实现
│       │   ├── __init__.py
│       │   ├── main.py          # ranger-morph 命令入口
│       │   └── commands/        # 具体子命令模块
│       │       ├── convert.py
│       │       ├── inspect.py
│       │       └── benchmark.py
│       │
│       ├── core/                # 核心抽象 & 主流程
│       │   ├── __init__.py
│       │   ├── ir.py            # 内部统一 IR 定义（Graph / Node / Tensor 等）
│       │   ├── registry.py      # 前端/后端注册表
│       │   ├── pipeline.py      # 转换主流程编排
│       │   └── config.py        # 全局配置结构 & 解析
│       │
│       ├── frontends/           # “读入模型”的适配层（各框架 -> IR）
│       │   ├── __init__.py
│       │   ├── pytorch_loader.py
│       │   ├── onnx_loader.py
│       │   ├── tensorflow_loader.py
│       │   ├── gguf_loader.py
│       │   └── ……
│       │
│       ├── backends/            # “导出模型”的适配层（IR -> 各目标格式/引擎）
│       │   ├── __init__.py
│       │   ├── onnx_exporter.py
│       │   ├── tensorrt_exporter.py
│       │   ├── openvino_exporter.py
│       │   ├── mnn_exporter.py
│       │   └── gguf_exporter.py
│       │
│       ├── passes/              # 转换中间过程的优化/变换 pass
│       │   ├── __init__.py
│       │   ├── fold_constants.py
│       │   ├── fuse_layers.py
│       │   ├── quantization.py
│       │   └── layout_transform.py
│       │
│       ├── utils/               # 通用工具
│       │   ├── __init__.py
│       │   ├── logging.py
│       │   ├── file_io.py
│       │   ├── torch_utils.py
│       │   ├── onnx_utils.py
│       │   └── temp_dir.py
│       │
│       └── plugins/             # 未来社区/自己扩展的插件
│           ├── __init__.py
│           └── README.md
│
├── examples/                    # 使用示例 (脚本 / notebook)
│   ├── basic_convert.md
│   ├── pytorch_to_onnx.py
│   ├── asr_model_to_trt.py
│   └── vision_model_to_gguf.py
│
├── configs/                     # 默认与示例配置文件
│   ├── default.yaml
│   ├── pytorch_to_onnx.yaml
│   └── onnx_to_trt.yaml
│
├── tests/                       # 单测 & 集成测试
│   ├── __init__.py
│   ├── test_cli.py
│   ├── test_frontends.py
│   ├── test_backends.py
│   ├── test_passes.py
│   └── data/
│       └── tiny_models/         # 很小的测试模型权重/结构
│
├── scripts/                     # 开发/发布辅助脚本
│   ├── run_tests.sh
│   ├── format.sh
│   ├── gen_docs.sh
│   └── benchmark_all.sh
│
├── docs/                        # 文档（后面可挂 readthedocs 或 mkdocs）
│   ├── index.md
│   ├── installation.md
│   ├── cli_usage.md
│   ├── api_reference.md
│   ├── converters_matrix.md     # 支持矩阵文档（哪种->哪种）
│   └── roadmap.md
│
├── pyproject.toml               # 推荐用 pyproject 管理构建 & 依赖
├── README.md
├── LICENSE
├── CONTRIBUTING.md              # 开源贡献指南
└── .gitignore
