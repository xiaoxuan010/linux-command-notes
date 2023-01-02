# 备忘录：Linux指令

### 实时打印文件

`tail -f 文件名.log`



### 后台运行相关

#### 输出重定向

覆盖：`>`

追加：`>>`

#### 普通后台运行

`Ctrl+Z`将当前任务**暂停**并移至后台

`jobs`查看后台任务及编号

`fg %编号`返回前台

`kill %编号`关闭任务



退出console后，后台任务会停止



#### 不中断后台运行

完整命令：`nohup ./可执行文件 > ./日志输出.log &`

`jobs`查看后台任务及编号

` ps -ef |grep 可执行文件 `查看可执行文件进程

退出console后，后台任务不停止；再次连接console后，无法用`jobs`查看任务，可以用` ps -ef |grep 可执行文件 `查看任务。



### echo输出

#### 输出时间日志

`echo -e "\n$(date) 服务器启动" >> server.log`



### FFMpeg

#### 显示输入设备

`ffmpeg -list_devices true -f dshow -i dummy`

dummy参数含义未知



#### RTSP 麦克风 音频 推流

参考命令：`ffmpeg -f dshow -i audio="麦克风阵列 (Synaptics Audio)" -ab 192k -f rtsp "rtsp://106.55.41.100:8554/pc"`

`audio=上步获取的设备名称`，亦可作`video=设备名称,audio=设备名称`

`-ab 192k`比特率，`-ar 44100`采样率，`-ac 2`声道



### FFplay

#### 无缓存播放

`ffplay -fflags nobuffer -x 640 %addr%`

-x（或-y）指定窗口大小，若只指定一个则会自动匹配。



### Bash 窗口快捷键

#### 移动光标

- `ctrl+a`: 移到行首（ahead）
- `ctrl+e`: 移到行尾（end）
- `alt+b`: 前移一个单词
- `alt+f`: 后移一个单词
- `ctrl+xx`: 行首到当前光标替换
- `ctrl+b`: 前移一个字符(backward)
- `ctrl+f`: 后移一个字符(forward)

#### 各种删除

- `ctrl+u`: 删除光标左边所有
- `ctrl+k`: 删除光标右边所有
- `ctrl+l`: 清屏
- `alt+d`: 删除当前光标到临近右边单词开始(delete)
- `ctrl+w`: 删除当前光标到临近左边单词结束(word)
- `ctrl+h`: 删除光标前一个字符（相当于backspace）
- `ctrl+d`: 删除光标后一个字符（相当于delete）

#### 历史命令

- `ctrl+n`: 下一条命令
- `ctrl+p`: 上一条命令
- `alt+n`: 下一条命令（例如输入`ls`, 然后按'alt+n', 就会找到历史记录下的`ls`命令）
- `alt+p`: 上一条命令（跟`alt+n`相似）
- `ctrl+r`: 进入历史查找命令记录， 输入关键字。 多次按返回下一个匹配项

#### 编辑命令

- `alt+.`: 粘帖最后一次命令最后的参数（通常用于`mkdir long-long-dir`后, `cd`配合着`alt+.`）
- `ctrl+shift+c`: 复制（相当于鼠标左键拖拽）
- `ctrl+shift+v`: 粘贴（相当于鼠标中键）
- `shift+PageUp`: 向上翻页
- `shift+PageDown`: 向下翻页