# 创建用于scapy运行的python虚拟环境，隔离当前环境包版本冲突

1. 导出scapy包。

   - 在当前目录创建一个scapy_offline目录。

   - 在当前目录编辑`vim requirements.txt`，文件内容为

     ```
     scapy==2.4.4
     ```

   - 在当前scapy_offline目录执行

     ```
     python3 -m pip download -r requirements.txt -d .
     ```

   这样当前目录就可以得到scapy的包了。

2. 创建一个虚拟环境

   ```
   //创建myenv虚拟环境，当前目录会创建出myenv子目录
   python3 -m venv ./myenv
   //激活myenv环境
   source ./myenv/bin/activate
   //安装scapy
   pip install --no-index --find-links=. -r requirements.txt
   //检验scapy是否正常安装
   python3 -c "from scapy.all import *; print('Scapy loaded successfully')"
   
   ```

3. 可以试着运行攻击脚本了。

   我们攻击脚本只依赖于scapy库。