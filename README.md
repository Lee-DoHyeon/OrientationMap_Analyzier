# OrientationMap_Analyzier
Orientation Map Analysis for Challenge @2024 [Computational Neuroscience Winter School](https://www.cbrain.org/%ED%95%99%EC%88%A0%ED%96%89%EC%82%AC/2024-%EA%B2%A8%EC%9A%B8%ED%95%99%EA%B5%90)  

`Team Name`: Team 1 Loki

`Team Members`: Oh Hong-seok (Team Leader), Bang Hee-yeon, Lee Do-hyun, Lee Je-yoon, Cho Soo-bin

`Answer`: **[6 3 7 8 5 1 2 4 9 10]**

### **Key Assumptions and Claims**

<aside>
🌱 **Assumption 1** Stimuli are **randomly** provided. `Verified`

**Assumption 2** The number of stimuli provided in the experiment will be **similar**. `Verified`

</aside>

<aside>
🤚🏻 **Claim 1** Each neuron has its unique characteristic that reacts **on average** to stimuli.

**Claim 2** The unique average characteristic of each neuron's stimulus exhibits **periodicity**.

**Claim 3** The **average firing pattern** according to each neuron's angle stimulus can be explained by (1) preferred angle $\theta_0$, (2) sensitivity to stimulus $I_0$, (3) error term $\text{offset}`.

**Claim 4** The distribution of waiting times until each neuron fires can be explained by an **exponential distribution**, and accordingly has (1) a unique 𝜆 parameter.

</aside>

### **Problem-solving Process**

Through the exploratory data analysis process, we analyzed the data in various ways. We discovered that each neuron in V1 has its unique characteristic that reacts on average to stimuli. When we checked the average firing amount according to the stimulus angle of the cells in the polar coordinate system, it showed a pattern with a periodicity of π. We assumed a trigonometric function with a period of π for the characteristic of each neuron's firing in the sample data period ([50-350]s) and test data period ([400-700]s) for curve fitting reflecting this characteristic(`Claim 3`). The modeling equation is as follows ($i$ is the cell index):

$$
N^i_{during\ 300s}(t)=I^i_0\cdot \cos(2(\theta-\theta^i_0))+\text{offset}^i
$$

We tried to cluster the cells of the sample data and test data based on the similarity of the parameters $(\theta_0, I_0)$ of the fitting curve in the sample data and test data.

**K-means clustering**

All cells except the combination (10, 10) of Train and Test Cells were matched independently with the cells of the sample data.

!https://prod-files-secure.s3.us-west-2.amazonaws.com/273a69d2-3ce8-47b7-a60a-02fe38ea484e/dcb87a64-4b1a-4738-a7f8-d991e59ae6e2/Untitled.png

**Nearest Neighborhood clustering**

All cells except the combination (8, 4) of Train and Test Cells were matched independently with the cells of the sample data.

!https://prod-files-secure.s3.us-west-2.amazonaws.com/273a69d2-3ce8-47b7-a60a-02fe38ea484e/3d939649-6237-43d7-b453-d1bd8f87549c/Untitled.png

On the other hand, for the matching of combinations (10, 10), (8, 4), additional verification was performed by fitting the inter-spike interval(ISI) distribution to the Exponential curve. Each cell has a 𝜆 parameter, and we confirmed that the combinations (10, 10), (8, 4) in question have unique values.

<aside>
❗ $\lambda$ parameter for train 6 th cell & test  1 th cell: 5.99   |   5.48

$\lambda$ parameter for train 3 th cell & test  2 th cell: 7.51   |   6.55

$\lambda$ parameter for train 7 th cell & test  3 th cell: 19.61   |   17.97

$\lambda$ parameter for train 8 th cell & test  4 th cell: **0.80**   |   **1.18**

$\lambda$  parameter for train 5 th cell & test  5 th cell: 5.02   |   5.46

$\lambda$ parameter for train 1 th cell & test  6 th cell: 4.04   |   2.98

$\lambda$ parameter for train 2 th cell & test  7 th cell: 6.64   |   6.80

$\lambda$ parameter for train 4 th cell & test  8 th cell: 2.51   |   3.14

$\lambda$ parameter for train 9 th cell & test  9 th cell: 2.51   |   1.78

$\lambda$ parameter for train 10 th cell & test  10 th cell: **17.23**   |   **16.63**

</aside>


### Acknowledgments

We enjoyed the meal! Thanks to committee, we were able to have a happy time😊  

