## Research Experience 

Throughout my university years, I have actively pursued my interests, especially during my coursework in communications principles, where I excelled and received the Excellent Subject Award. Additionally, I joined the Chung Yuan University RF Lab as a research assistant, providing me with practical learning and research opportunities.

1. Research Assistant Experience
    - MR Mechanical Arm Teaching System (MetaACES Acceptance)  
    I was involved in the development of a system using HoloLens 2 aimed at instructing users on how to operate robotic
    arms. I was responsible for the system’s design, development, and testing, and actively participated in integrating real robotic arm functionalities. This project deepened my understanding of the integration between mixed reality technologies and mechanical control, along with the challenges and solutions in practical applications.

    - Campus VR Tour System (IEEE ECICE Acceptance)  
    In this project, I collaborated with international students to develop a digital twin system for the campus. I served as the team leader, responsible for system design, development, and coordinating the progress. Our work was successfully presented at IEEE ECICE, where we received the Best Paper award.

    - Sidelobe Reduction (IEEE ICASI Acceptance)  
    I contributed to a project focused on optimizing antenna performance. We proposed a new antenna architecture that optimizes the farfield without adjusting the signal processing, thus reducing sidelobe issues. My role primarily involved theoretical analysis, and our findings were published at IEEE ICASI.

    - Research on Beamforming Array Optimization  
    I am currently engaged in research on optimizing beamforming arrays without altering the original antenna structures, aiming to achieve signal processing objectives by adjusting the antenna arrangements. This research is ongoing.

    - 8x8 MIMO Mobile Antenna Integration with Machine Learning  
    Furthermore, I am involved in a project on MIMO mobile antennas, where post- design, we use machine learning techniques to optimize the antenna spacing to enhance system performance and efficiency.

2. VLSI Design Experience
    - VLSI System Design Internship Course(Yu-Hsin, Inc.)  
    I learned to operate the Laker layout tool, understood industry-standard layout guidelines (DRC, LVS, PEX), and practiced circuit layout.

    - Chung Yuan University IC Summer Camp  
    I acquired skills in Full Custom Design, starting from circuit design using Virtuoso, to Laker layout, and finally verification with Calibre.


## Extracurricular Activities

1. IC design camp  
    在參加了由中原電子所舉辦的IC設計營隊後，我對IC設計有了更深入的了解。這個營隊涵蓋了以下幾個重要環節：

    1. **電路設計 (Virtuoso)**
    2. **電路模擬 (Hspice)**
    3. **Layout設計 (Laker/Virtuoso)**
    4. **Calibre驗證 (DRC/LVS/PEX)**

![test](images/IC_design.png)

這個活動讓我對於Full Custom Design有了一個大致的了解，學會了製成檔的意義及如何操作相關的設計軟體。  

2. 予新科技VLSI實習課程
    在參加了IC設計營隊之後，我對IC設計產生了濃厚的興趣。為了進一步深入學習這一領域，我選擇加入了中原大學電子系鐘文耀教授開設的課程。該課程與予新科技合作，主要教授業界實際的佈局方法和技術。這段學習經歷不僅增強了我的專業知識，還讓我對IC設計的實踐應用有了更深入的瞭解。  

3. 龜山生態展
    此外，我還積極參與了許多與地方文化相關的活動。這些活動包括瞭解桃園的在地文化、探索洋樓的歷史以及欣賞傳統歌仔戲。我還有幸採訪了臺灣歌仔戲首席乾旦，通過這些經歷，我對舊文化的保存與新文化的影響有了更深的興趣。

4. 5G產業新星計畫
    在這個計畫中我用NVIDIA  Jestson nano來做串流影像的辨識。








### 反運動演算法

在機械手臂的控制中，反運動學（Inverse Kinematics, IK）是一個極為重要的問題。反運動學的目標是根據機械手臂末端效應器（end-effector）的目標位置和姿態，計算出各個關節的運動參數，使機械手臂能夠精確地達到指定的位置。這一問題在機器人學和計算機圖形學中都有廣泛的應用。在本研究中，反運動學演算法主要應用於IK模式，模擬操作員在一定距離下使用指示點來控制機械手臂的運動。

#### 基本原理與目標函數

反運動學的基本原理涉及構建目標函數，該函數表示機械手臂末端位置與目標位置之間的距離。通過最小化這一目標函數，可以確定各個關節的運動參數。假設機械手臂具有 \( n \) 個自由度（關節），每個關節的角度為 \( q_i \)，機械手臂的末端位置為 \( \mathbf{P} \)，目標位置為 \( \mathbf{T} \)。則目標函數 \( f \) 可以表示為：

\[ f(\mathbf{q}) = \|\mathbf{P}(\mathbf{q}) - \mathbf{T}\| \]

其中，\( \mathbf{q} = [q_1, q_2, \ldots, q_n] \) 表示所有關節的角度向量。

#### 梯度下降法

梯度下降法是一種常用的優化技術，用於調整機械手臂的關節角度，使其末端位置逐漸接近目標點。梯度下降法通過計算目標函數相對於各個關節角度的梯度來進行迭代優化。梯度的計算可以使用Jacobian矩陣來實現。

#### Jacobian矩陣

Jacobian矩陣 \( \mathbf{J} \) 是一個描述目標函數相對於關節角度的偏導數的矩陣，用於估算每個關節角度變化對末端位置變化的影響。假設機械手臂的末端位置 \( \mathbf{P} \) 為 \( [x, y, z] \)，則Jacobian矩陣可以表示為：

\[ \mathbf{J} = \begin{bmatrix}
\frac{\partial x}{\partial q_1} & \frac{\partial x}{\partial q_2} & \cdots & \frac{\partial x}{\partial q_n} \\
\frac{\partial y}{\partial q_1} & \frac{\partial y}{\partial q_2} & \cdots & \frac{\partial y}{\partial q_n} \\
\frac{\partial z}{\partial q_1} & \frac{\partial z}{\partial q_2} & \cdots & \frac{\partial z}{\partial q_n}
\end{bmatrix} \]

#### 迭代優化過程

在每次迭代中，根據當前的關節角度計算目標函數的梯度，並根據梯度對關節角度進行更新。具體更新公式如下：

\[ \mathbf{q}_{\text{new}} = \mathbf{q}_{\text{old}} - \alpha \mathbf{J}^T \mathbf{e} \]

其中，\( \alpha \) 是學習率，控制每次迭代的步長；\( \mathbf{e} = \mathbf{P}(\mathbf{q}) - \mathbf{T} \) 是目標函數的誤差。

#### 收斂條件

迭代過程會持續進行，直到目標函數的值小於設定的閾值，即：

\[ \|\mathbf{P}(\mathbf{q}) - \mathbf{T}\| < \epsilon \]

其中，\( \epsilon \) 是預先設定的收斂閾值，用於控制迭代的精度。

#### 應用於機械手臂控制

在本研究中，梯度下降反運動學算法被應用於IK模式中。該模式通過指示點來控制機械手臂的運動，使其末端達到目標位置。具體步驟包括：

1. **設置初始關節角度**：初始化機械手臂各關節的角度 \( \mathbf{q}_0 \)。
2. **計算Jacobian矩陣**：根據當前關節角度計算Jacobian矩陣 \( \mathbf{J} \)。
3. **計算目標函數誤差**：計算當前末端位置與目標位置的誤差 \( \mathbf{e} \)。
4. **更新關節角度**：使用梯度下降法更新關節角度 \( \mathbf{q} \)。
5. **檢查收斂條件**：檢查目標函數是否滿足收斂條件，若否則返回步驟2繼續迭代。

這一過程通過多次迭代，最終使機械手臂末端位置精確到達目標點，實現高效且準確的遠程操作控制。

#### 結論

反運動學演算法在機械手臂控制中的應用，顯著提高了操作的精確性和效率。通過梯度下降法的應用，能夠在短時間內計算出最佳的關節角度，使機械手臂能夠精確達到目標位置。本研究所設計的IK模式，不僅模擬了實際工業環境中的操作場景，還為學員提供了一個直觀且有效的學習工具，有助於提升其操作技能和應變能力。