# demo

1. 进入 Jenkins 容器并生成密钥
首先，你需要进入正在运行的 Jenkins 容器内部。
进入容器：
在终端执行以下命令（请将 jenkins 替换为你实际的容器名或 ID）：
bash

编辑



docker exec -it jenkins /bin/bash
生成 SSH 密钥对：
在容器内的 Shell 中，执行生成密钥的命令。为了方便管理，建议指定一个文件名（例如 github_key），避免与可能存在的默认密钥冲突。
bash

编辑



ssh-keygen -t rsa -b 4096 -C "your_email@example.com" -f ~/.ssh/github_key
-t rsa -b 4096: 指定加密类型和长度。
-C "your_email...": 注释，通常是邮箱，用于标识该密钥。
-f ~/.ssh/github_key: 指定密钥保存的路径和文件名。
查看公钥内容：
生成后，你需要将公钥（.pub 文件）的内容复制出来。
bash

编辑



cat ~/.ssh/github_key.pub
复制输出的全部内容（以 ssh-rsa 开头，以你的邮箱结尾的一长串字符）。
