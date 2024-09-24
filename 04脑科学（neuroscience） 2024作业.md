## 第一次作业 计算机编程：动作电位HH模型
### 知识背景 
#### 1. 神经元
   神经元是神经系统的基本单元，负责接收、处理和传递信息。它们通过电信号和化学信号来与其他神经元、肌肉和腺体等进行通信。以下是对神经元的基本特征以及其电容特性和静息膜电位的详细解释。
- 细胞体（Soma）：神经元的主要部分，包含细胞核和大部分细胞器，负责维持细胞的生命活动。
- 树突（Dendrites）：从细胞体延伸出的多个分支，负责接收来自其他神经元的信号。
- 轴突（Axon）：从细胞体延伸的长纤维，负责将电信号传递到其他神经元或效应器（如肌肉）。
   
图：理想化的哺乳动物神经元
<img width="888" alt="image" src="https://github.com/user-attachments/assets/44b23818-b44a-4e2b-aeb7-5fe52458ea24">

3. 细胞膜结构
  <img width="590" alt="image" src="https://github.com/user-attachments/assets/cee9ce43-c209-4983-ba57-70c641112e68">

4. 神经元电容特性和静息膜电位特点实现了一种神经元细胞膜电极性的有序特性
<img width="771" alt="image" src="https://github.com/user-attachments/assets/046c0667-21e8-4e2a-ac2c-ce6c38218896">

（1）神经元的电容特性

- 电容（Capacitance）：神经元细胞膜可以被视为一个电容器，能够储存电荷。膜的电容特性决定了神经元对电流变化的反应。
- 膜电容（Cm）：膜电容是指细胞膜能储存的电荷量，通常以法拉（F）为单位。膜电容的大小受膜的厚度、介电常数和膜表面积的影响。
- 时间常数（τ）：电容和电阻的乘积决定了膜电位变化的速度。时间常数越大，膜电位变化越慢。时间常数的公式为：

\tau = R_m \cdot C_m
其中 ( R_m ) 是膜电阻， C_m  是膜电容。

（2）静息膜电位

- 静息膜电位（Resting Membrane Potential）：神经元在未被刺激时，膜内外电位差通常在 -70 mV 到 -90 mV 之间。这种电位差是由于细胞膜对钠（Na⁺）、钾（K⁺）等离子的不同渗透性造成的。
- 离子浓度：
- 细胞内：钾离子浓度较高，钠离子浓度较低。
- 细胞外：钠离子浓度较高，钾离子浓度较低。
- 钾通道：静息膜电位主要由钾通道控制，膜在静息状态下对钾离子更为渗透，导致钾离子向外流动，从而形成负电位。

（3）有序特性与电极性

- 电极性（Polarity）：神经元膜的有序特性体现在膜内外电位差的存在。神经元在静息状态下的负电位是其正常功能的基础。
- 动作电位的产生：当神经元受到刺激时，膜电位会去极化，形成动作电位。这种有序的电位变化是信息传递的基础。



### Function: alphabeta

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
