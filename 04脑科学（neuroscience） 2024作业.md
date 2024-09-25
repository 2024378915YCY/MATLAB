## 第二章 细胞机制与认知（含第一次作业 计算机编程：动作电位HH模型）
### 一、神经系统的细胞
#### 1. 神经元
   神经元是神经系统的基本单元，负责接收、处理和传递信息。它们通过电信号和化学信号来与其他神经元、肌肉和腺体等进行通信。以下是对神经元的基本特征以及其电容特性和静息膜电位的详细解释。
- 细胞体（Soma）：神经元的主要部分，包含细胞核和大部分细胞器，负责维持细胞的生命活动。
- 树突（Dendrites）：从细胞体延伸出的多个分支，负责接收来自其他神经元的信号。
- 轴突（Axon）：从细胞体延伸的长纤维，负责将电信号传递到其他神经元或效应器（如肌肉）。
   
图：理想化的哺乳动物神经元
<img width="888" alt="image" src="https://github.com/user-attachments/assets/44b23818-b44a-4e2b-aeb7-5fe52458ea24">

#### 2.胶质细胞
**胶质细胞**（Glial cells）是中枢神经系统和外周神经系统中的非神经元细胞。它们在支持和保护神经元方面起着重要作用，负责维持神经元的环境、提供营养、清除废物，以及帮助维持血脑屏障等功能。胶质细胞的数量远远大于神经元，是其10倍左右。

胶质细胞的主要类型包括：

1. **星形胶质细胞**（Astrocytes）：负责支持和调节神经元之间的通信，维持血脑屏障，调节血流，回收神经递质等。
2. **少突胶质细胞**（Oligodendrocytes）：主要功能是为中枢神经系统的神经元轴突形成**髓鞘**，从而加快神经信号的传导。
3. **小胶质细胞**（Microglia）：中枢神经系统中的免疫细胞，起到吞噬病原体和清除损伤细胞的作用。
4. **卫星细胞**（Satellite cells）：存在于外周神经系统中，支持感觉神经元并调节其微环境。
5. **施万细胞**（Schwann cells）：负责为外周神经系统中的轴突形成髓鞘，功能类似少突胶质细胞。

胶质细胞在神经系统的功能中至关重要，尤其在神经保护、修复及信息传导方面。此外，胶质细胞还与神经系统疾病（如阿尔茨海默病、帕金森病和多发性硬化症）的病理机制密切相关。

<img width="967" alt="image" src="https://github.com/user-attachments/assets/554ae9a7-10a3-4d59-94d6-67ec366a438f">


问题：为什么髓鞘导致神经信号传递减慢甚至完全阻断？

### 二、神经信号
神经元的功能是分析和传递信息。
#### 1. 神经元之间的信息交流主要通过以下几个步骤进行：

- **动作电位的产生**：当神经元受到（化学或物理）刺激时，膜电位发生变化，达到阈值，触发动作电位（电信号）。这一过程涉及钠离子（Na⁺）和钾离子（K⁺）的流入和流出，引发电荷变化。神经元的发放率是10个动作电位每秒。
- **动作电位的传播**：动作电位沿着神经元的轴突快速传播，直到到达轴突末端（突触前末端）。动作电位是主动电信号，有利于长距离信息交流。
- **化学信号的释放**：当动作电位到达突触前末端时，促使钙离子（Ca²⁺）进入突触前末端，刺激神经递质（化学信号）从突触小泡释放到突触间隙。
- **神经递质的接收**：神经递质穿过突触间隙，与下一个神经元的突触后膜上的特定受体结合。
- **信号传递**：受体结合后，触发突触后神经元的膜电位变化，可能引发新的动作电位，继续传递信号。

#### 2.神经元细胞膜和膜电位的特性
1. **神经元细胞膜的特性**：
- 磷脂双分子层结构：细胞膜由磷脂分子组成的双层膜构成，具有疏水性内核和亲水性外层。这使得大多数带电离子无法直接通过细胞膜，形成了一个屏障。

  图 细胞膜结构
  <img width="590" alt="image" src="https://github.com/user-attachments/assets/cee9ce43-c209-4983-ba57-70c641112e68">

  
- **选择性渗透性性**：细胞膜嵌有特定的离子通道和泵，允许特定的离子（如钠离子 Na⁺、钾离子 K⁺、氯离子 Cl⁻ 等）进出细胞。这些通道通过控制离子流动来调节膜电位。

  <img width="506" alt="image" src="https://github.com/user-attachments/assets/205f486f-3bff-4236-9683-7d8281606611">


- **钠-钾泵**：通过主动运输，钠-钾泵将 3 个 Na⁺ 离子泵出细胞，并将 2 个 K⁺ 离子泵入细胞。这个过程消耗 ATP 能量，维持细胞内外的离子浓度差异。神经元细胞膜外是较高浓度的Na+，细胞内则是较高浓度的K+。

<img width="434" alt="image" src="https://github.com/user-attachments/assets/f669ea30-84b3-47b6-88c4-932e4fa15a2d">



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
<img width="617" alt="image" src="https://github.com/user-attachments/assets/6783003d-5993-4e43-82f3-c3cbf4870405">


<img width="490" alt="image" src="https://github.com/user-attachments/assets/d7136cee-3040-4299-9c52-5138ca6967e7">

<img width="770" alt="image" src="https://github.com/user-attachments/assets/5b11bcc0-34c1-4b66-b0be-cc1e033f9a30">

- 静息膜电位：神经元在未被激活时处于静息状态，膜内带负电，膜外带正电。静息膜电位通常在 -70 毫伏左右，主要由钾离子的通透性和钠-钾泵的作用维持。
- 去极化：当神经元受到刺激时，钠通道开放，Na⁺ 大量流入细胞，使膜电位变得不那么负，这个过程称为去极化。如果膜电位达到阈值，动作电位就会被触发。
- 动作电位：动作电位是一个短暂的、快速的电位反转。当膜电位达到阈值后，钠离子快速进入细胞，膜电位反转为正值（约 +30 毫伏）。
- 复极化：在动作电位达到峰值后，钠通道关闭，钾通道开放，K⁺ 离子流出细胞，使膜电位恢复为负值，进入复极化阶段。
- 超极化：在复极化后，膜电位可能短暂变得比静息电位更负，这称为超极化，随后通过钠-钾泵和钾通道的调整恢复到静息电位。

**不应期**（Refractory Period）是指神经元在动作电位后暂时无法再次产生动作电位的时期。它确保了动作电位单向传播，并限制了神经元的发放频率。主要分为两种类型：
-  **绝对不应期**（Absolute Refractory Period）：
   - 在此期间，无论施加多大的刺激，神经元都无法产生新的动作电位。
   - 绝对不应期发生在动作电位的去极化和复极化初期，此时钠通道已被激活并随后被失活，无法重新开放。
   - 这个阶段保证了动作电位只能单向传播，即从细胞体到轴突末端，而不会回流。

- **相对不应期**（Relative Refractory Period）：
   - 在相对不应期期间，神经元仍然可以产生新的动作电位，但需要比平常更强的刺激。
   - 这个阶段发生在复极化的后期及超极化阶段，钾离子仍然大量流出细胞，膜电位比静息膜电位更负（超极化状态）。因此，只有较强的刺激才能使膜电位再次达到阈值。
  
功能：不应期的存在防止了神经元过度频繁地发放动作电位，确保信号传递的清晰性与稳定性。同时，它通过限制神经信号的频率，调节信息在神经系统中的处理速度。

### 三 Hodgkin-Huxley (HH) 模型

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







### 作业

#### 1. 静息膜电位计算
**Goldman-Hodgkin-Katz (GHK) 方程**，也称为**Goldman方程**，用于计算细胞膜的**平衡电位**或**膜电位**，考虑了多种离子的相对通透性。它是经典的**Nernst方程**的扩展，适用于多种可透过膜的离子，而不仅限于单一离子。

- GHK方程的基本形式：

对于一般的细胞膜电位，GHK方程可以写为：

$$ V_m = \frac{RT}{F} \ln \left( \frac{P_{\text{Na}^+}[\text{Na}^+]{\text{out}} + P{\text{K}^+}[\text{K}^+]{\text{out}} + P{\text{Cl}^-}[\text{Cl}^-]{\text{in}}}{P{\text{Na}^+}[\text{Na}^+]{\text{in}} + P{\text{K}^+}[\text{K}^+]{\text{in}} + P{\text{Cl}^-}[\text{Cl}^-]_{\text{out}}} \right) $$




其中：

- $\( V_m \)$ 是膜电位（以伏特为单位）。
- $\( R \)$ 是气体常数（8.314 J/(mol·K)）。
- $\( T \)$ 是绝对温度（以开尔文为单位，通常是37°C，即310 K）。
- $\( F \)$ 是法拉第常数（96485 C/mol）。
- $( P_K )$, $( P_{Na} )$, $( P_{Cl} )$：钾、钠和氯离子的渗透率
- $([K^+]_i)$, $([K^+]_o)$：膜内、膜外钾离子浓度
- $([Na^+]_i)$, $([Na^+]_o)$：膜内、膜外钠离子浓度
- $([Cl^-]_i)$, $([Cl^-]_o)$：膜内、膜外氯离子浓度


**方程解释：**

- **通透性（P）**：方程中考虑了不同离子（如 Na⁺、K⁺ 和 Cl⁻）通过细胞膜的通透性。这反映了不同离子通过膜的容易程度。
   
- **浓度梯度**：每种离子的内外浓度都会影响膜电位。钠和钾是最重要的离子，它们的浓度梯度决定了静息膜电位，而氯离子的浓度通常较为稳定，起到平衡作用。

- **温度**：温度通过 \( \frac{RT}{F} \) 的项来影响方程，通常在生物系统中，温度被认为是恒定的。

**GHK方程的应用：**
- **静息膜电位**：GHK方程常用于计算细胞的静息膜电位，尤其是神经元或肌肉细胞。静息膜电位是膜对钾、钠和氯等离子的通透性不同的结果。
- **动作电位的产生**：在动作电位过程中，钠和钾通道的通透性发生巨大变化，因此 GHK 方程可以帮助描述这些离子流动对膜电位的影响。

**题目**：  
对表格给出的膜内外离子浓度数据，当温度T从6 0C 每隔10C 逐渐升高到40 0C，神经元细胞膜的静息膜电位如何
变化？计算并给出随温度T变化曲线。（假设渗透率的比率是PK：PNa：PCl = 1：0.03：0.1保存不变）

![image](https://github.com/user-attachments/assets/197312c3-4cc7-491c-9341-3fc0811c420c)



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
