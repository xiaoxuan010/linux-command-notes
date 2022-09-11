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

`-ab 192k`比特率，`-ar 44100`采样率，`-ac 2`声道数









