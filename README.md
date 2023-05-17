# Machine-Failure-Prediction

The ability to predict machine failures, as well as the nature of the failure, is essential for Generation 4.0 industries. This is because the repair or replacement of a faulty machine can often be much more expensive than the cost of replacing a single component. Therefore, the installation of sensors that monitor the state of machines and collect the appropriate data can lead to significant savings for industries.

In this project, we use the AI4I Predictive Maintenance Dataset from the UCI Repository to conduct an analysis that aims to address the aforementioned needs. In particular, the work is presented in a manner that is consistent with a typical Machine Learning application. First, the dataset is explored to gain a deeper understanding of the ground truth. Then, some preprocessing techniques are applied to prepare the data for the algorithms that we will use to make our predictions. We consider two main tasks: the first is to determine whether a generic machine is about to fail, and the second is to determine the nature of the fault.

# Data Description
Since real predictive maintenance datasets are generally difficult to obtain and in particular difficult to publish, the data provided by the UCI repository is a synthetic dataset that reflects real predictive maintenance encountered in industry to the best of their knowledge. The dataset consists of 10 000 data points stored as rows with 14 features in columns.

**UID**: This is a unique identifier that ranges from 1 to 10000.

**Product ID**: This consisting of a letter L, M, or H for low (60% of all products), medium (30%) and high (10%) as product quality variants and a variant-specific serial number

**Air temperature [K]**: This is the temperature of the air in the environment where the machine is operating. It is generated using a random walk process later normalized to a standard deviation of 2 K around 300 K.

**Process temperature [K]**: This is the temperature of the process that the machine is performing. It is generated using a random walk process normalized to a standard deviation of 1 K, added to the air temperature plus 10 K.

**Rotational speed [rpm]**: This is the speed at which the machine is rotating. It is calculated from a power of 2860 W, overlaid with a normally distributed noise.

**Torque [Nm]**: This is the amount of force that the machine is applying. It is normally distributed around 40 Nm with a standard deviation of 10 Nm and no negative values.

**Tool wear [min]**: This is the amount of time that the tool has been used. The quality variants H/M/L add 5/3/2 minutes of tool wear to the used tool in the process.

**Machine failure**: label that indicates, whether the machine has failed in this particular data point for any of the following failure modes are true. The machine failure consists of five independent failure modes:

**Tool Wear Failure (TWF)**: The tool will be replaced or fail at a randomly selected tool wear time between 200 and 240 minutes.

**Heat Dissipation Failure (HDF)**: Heat dissipation causes a process failure if the difference between the air and process temperatures is below 8.6 K and the tool's rotational speed is below 1380 rpm.

**Power Failure (PWF)**:The product of torque and rotational speed (in rad/s) equals the power required for the process. If this power is below 3500 W or above 9000 W, the process fails.

**Overstrain Failure (OSF)**: If the product of tool wear and torque exceeds 11,000 minNm for the L product variant (12,000 M, 13,000 H), the process fails due to overstrain.

**Random Failures (RNF)**: Each process has a chance of 0.1% to fail regardless of its process parameters.

If at least one of the above failure modes is true, the process fails and the ’machine failure’ label is set to 1. It is therefore not transparent to the machine learning method, which of the failure modes has caused the process to fail.
