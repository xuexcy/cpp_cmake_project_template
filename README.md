# cpp_cmake_project_template
## Build And Run
- `env_variable.sh`: 设置环境变量，如 cmake 工作目录、可执行文件存放的 bin 文件夹目录等
- `build.sh`: 编译所有 src/*.cc
- `run.sh`: 运行所有编译后的可执行文件，并将结果输出到 stdout 目录
- `build_one.sh`: 编译 src 目录下的一个 .cc 文件，具体编译哪一个文件取决于 `env_variable.sh` 中的 `default_execute_file` 环境变量。 这个脚本主要是自己修改、测试某个 .cc 代码的时候使用，该文件里没有调用 cmake，如果编译的相关依赖发生改变，请重新执行 `build.sh` 生成新的 makefile 文件
- `run_one.sh`: 执行一个编译结果，同 `build_one.sh` 一样，具体哪个取决于 `env_variable.sh` 中的 `default_execute_file`
- `src/*.cc`: 各个 main 文件
## tips
1. vscode clangd 插件:
  - 在 workspace 下设置 compile_command.json 路径
    `--compile-commands-dir=${workspaceFolder}/build_g++`
  - 通过 `g++ -v -E -x c++ - < /dev/null 2>&1 | grep -A1 '#include <...>'` 获取 g++ include 的路径，并进行设置
    `--extra-arg=-I/opt/homebrew/Cellar/gcc/14.2.0_1/include/c++/14`
2. [clang-format](https://github.com/xuexcy/personal_conf/tree/master/clang)

