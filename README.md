# Battery-HealthState-Pediction
多健康特征提取：
提取了时间特征、能量特征、增量容量 (IC) 特征，共计10个健康特征，以更准确地描述电池的衰退过程。
采用灰色关联分析 (GRA) 评估特征与SOH的相关性，确保特征的有效性。
改进的 LSTM 估计模型：
采用 改进量子粒子群优化 (IQPSO) 算法 来优化 LSTM 的超参数（隐藏层神经元数、学习率、迭代次数、dropout 等），提高模型的全局搜索能力和收敛速度。
实验验证：
使用 NASA 电池数据集，在不同放电条件和温度下验证模型性能。
SOH 估计的均方根误差 (RMSE) 低于 1%，比标准 LSTM、PSO-LSTM 和 QPSO-LSTM 方法更准确、鲁棒性更强。

数据集原始下载地址：https://ti.arc.nasa.gov/tech/dash/groups/pcoe/prognostic-data-repository/#battery
数据集有 4 个列：type，ambient_temperature，time，data

type：数据类型，包括 3 个类，分别为充电、放电和阻抗：charge， discharge 和 impedance

ambient_temperature：电池的工作温度，常温 24 度

time：充放电的时间，字符串格式

data：实时采集与电池性能相关的 6-7 组数据

a. type 为 'charge'，即充电状态下：

Voltage_measured：测量的电压
Current_measured：测量的电流
Temperature_measured：工作温度
Current_charge：充电器充电电流
Voltage_charge：充电器充电电压
Time：工作时间
b. type 为 'discharge'，即放电状态下：

Voltage_measured：测量的电压
Current_measured：测量的电流
Temperature_measured：工作温度
Current_load：在负载下测量的电流
Voltage_load：在负载下测量的电压
Time：工作时间
Capacity：放电至 2.7V 的电池容量 (Ahr)
c. type 为 'impedance'，即阻抗状态下：

Sense_current：传感器支路电流
Battery_current：电池支路电流
Current_ratio：以上电流的比率
Battery_impedance：根据原始数据计算的电池阻抗
Rectified_impedance：校准和平滑的电池阻抗
Re：估计电解液电阻
Rct：估计充电转移电阻
