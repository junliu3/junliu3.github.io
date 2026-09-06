#### 车载信号采集仪表盘（STM32F103 + HAL）｜2026.08

- 基于 STM32F103（HAL 库）实现车载信号采集仪表盘：定时器编码器模式采集转速、ADC 采样电位器 / 热敏电阻模拟油门开度与温度；
- 软件 I2C 驱动 OLED 实时显示仪表数据，实时刷新转速 / 油门 / 温度三项仪表数据；
- 实现超限报警：任一项超出设定阈值即驱动蜂鸣器告警，OLED 同步高亮提示；
- 覆盖定时器、ADC、I2C、GPIO 等核心外设，STM32CubeMX 工程搭建与 HAL 库外设配置。

#### 实时智能监控系统（C++17 + Qt + OpenCV）｜2026.07

- 基于 C++17 + Qt + OpenCV 实现多路实时监控系统，采用 HOG + SVM 行人检测（detectMultiScale 多尺度 + NMSBoxes 非极大值抑制），只识别人形目标、过滤光影 / 树叶等运动干扰，实时绘制边界框与置信度；
- 支持最多 9 路视频九宫格并发，每路独立 QThread 采集线程，通过信号槽（队列连接）跨线程安全通信，采集 / 检测与 UI 线程分离，界面流畅不卡顿；
- 实现人物触发自动录像，连续 3 秒无人自动停止，多路文件名带路号避免覆盖；运动防抖（连续 3 帧判定）避免状态栏闪烁；
- 基于 QTcpServer 实现 MJPEG 局域网推流（multipart/x-mixed-replace），同一 WiFi 下浏览器免装软件实时观看；无客户端时零编码开销、帧率上限 10fps 控制 CPU / 带宽。[[Code]](https://github.com/qrsxz/Smart-Surveillance)

#### 高并发 HTTP 服务器（C + epoll + 线程池）｜2026.03

- 基于 C 语言实现静态 HTTP 服务器，采用 epoll 事件驱动 + 线程池处理高并发请求；
- 支持 GET / HEAD / POST、断点续传（Range）、Keep-Alive 长连接、sendfile 零拷贝发送、目录浏览、CGI 动态接口、访问日志；
- 实现 HTTP 协议解析（请求行 / 头部 / 请求体）、URL 解码；
- ab 压测（10000 请求 / 100 并发）单机 QPS 达 1.8 万、零失败。[[Code]](https://github.com/junliu3/http-server)
