## 第一次作业 计算机编程：动作电位HH模型
### 知识背景 
#### 1. 神经元
   神经元是神经系统的基本单元，负责接收、处理和传递信息。它们通过电信号和化学信号来与其他神经元、肌肉和腺体等进行通信。以下是对神经元的基本特征以及其电容特性和静息膜电位的详细解释。
- 细胞体（Soma）：神经元的主要部分，包含细胞核和大部分细胞器，负责维持细胞的生命活动。
- 树突（Dendrites）：从细胞体延伸出的多个分支，负责接收来自其他神经元的信号。
- 轴突（Axon）：从细胞体延伸的长纤维，负责将电信号传递到其他神经元或效应器（如肌肉）。
   
图：理想化的哺乳动物神经元
<img width="888" alt="image" src="https://github.com/user-attachments/assets/44b23818-b44a-4e2b-aeb7-5fe52458ea24">

图 细胞膜结构
  <img width="590" alt="image" src="https://github.com/user-attachments/assets/cee9ce43-c209-4983-ba57-70c641112e68">

#### 2. 神经元电容特性和静息膜电位特点实现了一种神经元细胞膜电极性的有序特性
<img width="771" alt="image" src="https://github.com/user-attachments/assets/046c0667-21e8-4e2a-ac2c-ce6c38218896">

**（1）神经元的电容特性**

- 电容（Capacitance）：神经元细胞膜可以被视为一个电容器，能够储存电荷。膜的电容特性决定了神经元对电流变化的反应。
- 膜电容（Cm）：膜电容是指细胞膜能储存的电荷量，通常以法拉（F）为单位。膜电容的大小受膜的厚度、介电常数和膜表面积的影响。
- 时间常数（τ）：电容和电阻的乘积决定了膜电位变化的速度。时间常数越大，膜电位变化越慢。时间常数的公式为：

$$
\tau = R_m \cdot C_m
$$

其中：
- $\(\tau\)$ 是时间常数
- $\(R_m\)$ 是膜电阻
- $\(C_m\)$ 是膜电容

**（2）静息膜电位**

- 静息膜电位（Resting Membrane Potential）：神经元在未被刺激时，膜内外电位差通常在 -70 mV 到 -90 mV 之间。这种电位差是由于细胞膜对钠（Na⁺）、钾（K⁺）等离子的不同渗透性造成的。
- 离子浓度：
- 细胞内：钾离子浓度较高，钠离子浓度较低。
- 细胞外：钠离子浓度较高，钾离子浓度较低。
- 钾通道：静息膜电位主要由钾通道控制，膜在静息状态下对钾离子更为渗透，导致钾离子向外流动，从而形成负电位。

**（3）有序特性与电极性**

- 电极性（Polarity）：神经元膜的有序特性体现在膜内外电位差的存在。神经元在静息状态下的负电位是其正常功能的基础。
- 动作电位的产生：当神经元受到刺激时，膜电位会去极化，形成动作电位。这种有序的电位变化是信息传递的基础。

<img width="490" alt="image" src="https://github.com/user-attachments/assets/d7136cee-3040-4299-9c52-5138ca6967e7">

#### 3 Hodgkin-Huxley (HH) 模型

**1. HH模型简介**

Hodgkin-Huxley模型是描述神经元电生理活动的经典模型，首次提出于1952年。该模型通过方程描述了动作电位的产生机制，涉及膜电流的离子流动。

**2. 关键参数与方程**

HH模型的核心在于描述神经元膜电流（ $I_m$ ）的不同组成部分：

- 膜电流 $I_m$ 由三种离子的电流组成：

 $I_m = I_{Na} + I_{K} + I_{L}$

其中：
- $I_{Na}$：钠离子电流
- $I_{K}$：钾离子电流
- $I_{L}$：泄漏电流

离子电流方程：

- 钠离子电流：

$$
I_{Na} = g_{Na} \cdot m^3 \cdot h \cdot (V - V_{Na})
$$  

- 钾离子电流：

$$
I_{K} = g_{K} \cdot n^4 \cdot (V - V_{K})
$$

- 泄漏电流：

$$
I_{L} = g_{L} \cdot (V - V_{L})
$$


- 电导和离子平衡电位：
   - $g_{Na}$, $g_{K}$, $g_{L}$ ：分别是钠、钾和泄漏的最大电导（单位：mS/cm²）。
	•	$V_{Na}$, $V_{K}$, $V_{L}$ ：分别是钠、钾和泄漏的平衡电位（单位：mV）。

**3. 动作电位的形成**

<img width="386" alt="image" src="https://github.com/user-attachments/assets/c9940200-566c-4946-9d69-4a0b0f1b1d71">

- 去极化：当刺激到达阈值时，钠通道打开，Na+流入细胞，导致膜电位迅速上升。
- 再极化：在达到峰值后，钾通道打开，K+流出，膜电位下降。
- 超极化：K+通道关闭延迟，膜电位暂时下降至-80 mV，随后恢复静息状态。

**MATLAB代码示例**

```matlab
% Hodgkin-Huxley Action Potential Simulation
% 霍奇金-赫胥黎动作电位模拟

% Time parameters
% 时间参数
dt = 0.01;         % time step (ms) 时间步长（毫秒）
tfinal = 50;       % total simulation time (ms) 总模拟时间（毫秒）
time = 0:dt:tfinal; % time vector 时间向量

% Parameters for membrane potentials (mV)
% 膜电位参数（单位：毫伏）
V_rest = -70;      % Resting membrane potential 静息膜电位
V_threshold = -55; % Threshold potential 阈值电位
V_peak = 40;       % Peak potential during depolarization 去极化的峰值电位
V_hyperpolar = -90;% Hyperpolarization potential 超极化电位

% Initialize membrane potential array
% 初始化膜电位数组
V = V_rest * ones(1, length(time));

% Create a stimulation that crosses the threshold at t = 5 ms
% 创建一个在5毫秒时超过阈值的刺激信号
Istim = zeros(1, length(time));  
Istim(50:60) = 20; % Simulate stimulus at 5 ms 模拟在5毫秒时的刺激

% Membrane potential dynamics
% 膜电位的动态变化
for i = 2:length(time)
    % Simulate depolarization, repolarization, and hyperpolarization
    % 模拟去极化、再极化和超极化的过程
    if V(i-1) > V_threshold
        % Depolarization 去极化
        V(i) = V(i-1) + (V_peak - V(i-1)) * dt;
        % Transition to repolarization if peak is reached
        % 如果达到峰值，转入再极化阶段
        if V(i) >= V_peak
            V(i) = V_peak;
        end
    elseif V(i-1) == V_peak
        % Repolarization 再极化
        V(i) = V(i-1) - (V(i-1) - V_rest) * dt;
    elseif V(i-1) < V_rest
        % Hyperpolarization 超极化
        V(i) = V(i-1) + (V_rest - V_hyperpolar) * dt;
    end
    
    % Add stimulus effect
    % 加上刺激的影响
    V(i) = V(i) + Istim(i);
end

% Plot the membrane potential over time
% 绘制膜电位随时间的变化
figure;
plot(time, V, 'LineWidth', 2);
hold on;

% Highlight the different phases
% 突出显示不同的阶段
yline(V_rest, '--', 'Resting Potential', 'LabelHorizontalAlignment', 'left');
yline(V_threshold, ':', 'Threshold Potential', 'LabelHorizontalAlignment', 'left');
yline(V_peak, '-.', 'Peak Potential', 'LabelHorizontalAlignment', 'left');
yline(V_hyperpolar, '--', 'Hyperpolarization', 'LabelHorizontalAlignment', 'left');

% Label the axes
% 标记坐标轴
xlabel('Time (ms)'); % 时间（毫秒）
ylabel('Membrane Potential (mV)'); % 膜电位（毫伏）
title('Action Potential Simulation'); % 动作电位模拟
grid on;
```

**代码工作原理总结：**

- **dt**：设置时间步长，控制每次计算膜电位变化的时间间隔。
- **V_rest**：表示神经元的静息膜电位，在没有刺激时维持在一个稳定的负值。
- **V_threshold**：表示去极化的阈值电位，超过该值后神经元会产生动作电位。
- **V_peak**：去极化的峰值电位，代表动作电位的最大电位。
- **V_hyperpolar**：再极化后的超极化状态，电位比静息电







### 编程作业

This function calculates the alpha and beta functions used in the model of action potentials.

#### Parameters
- `v`: Membrane potential (in mV).
- `m`: Activation variable for sodium channels.
- `h`: Inactivation variable for sodium channels.
- `n`: Activation variable for potassium channels.

#### Returns
- `am`: Alpha parameter for activation variable `m`.
- `ah`: Alpha parameter for inactivation variable `h`.
- `an`: Alpha parameter for activation variable `n`.
- `bm`: Beta parameter for activation variable `m`.
- `bh`: Beta parameter for inactivation variable `h`.
- `bn`: Beta parameter for activation variable `n`.
- `gna`: Sodium conductance.
- `gk`: Potassium conductance.
- `gl`: Leakage conductance.

#### Code
```matlab
function [am, ah, an, bm, bh, bn, gna, gk, gl] = alphabeta(v, m, h, n)
    gnax = 120; % gNa max conductance, unit: mS/cm² % gNa 最大导电性，单位：mS/cm²
    gkx = 36;   % gK max conductance, unit: mS/cm² % gK 最大导电性，单位：mS/cm²
    glx = 0.3;  % gl leakage conductance, unit: mS/cm² % gl 漏导电性，单位：mS/cm² 

    % Calculate alpha functions
    am = -0.1 * (40 + v) / (exp(-(40 + v) / 10) - 1);
    ah = 0.07 * exp(-(v + 65) / 20);
    an = -0.01 * (v + 55) / (exp(-(55 + v) / 10) - 1);
    
    % Calculate beta functions
    bm = 4 * exp(-(v + 65) / 18);
    bh = 1 / (exp(-(35 + v) / 10) + 1);
    bn = 0.125 * exp(-(v + 65) / 80);
    
    % Calculate conductance 计算导电性
    gna = gnax * m^3 * h; % Sodium conductance 计算导电性
    gk = gkx * n^4;       % Potassium conductance 计算导电性
    gl = glx;             % Leakage conductance 计算导电性
end
```

### results
<img width="570" alt="image" src="https://github.com/user-attachments/assets/42b8a795-7ffe-42df-a6d3-8ad534026612">
