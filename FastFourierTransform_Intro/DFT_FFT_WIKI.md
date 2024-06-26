<div align="center">

# Understanding The Discrete and Fast Fourier Transform

</div>

## Section One: Understanding Discrete Fourier Transform (DFT)

### 1.1.0: A Refresher on the Unit Circle

To understand the DFT, you need to have a strong understanding of how the unit circle works, as it is the basis of how the DFT computes similarity. Every point on a sinusoidal function corresponds to the component of a vector on the unit circle, this goes for both the regular and complex unit circle. As the sinusoidal function progresses, the unit circle rotates counterclockwise to create a new value of each component and repeats every 2π radians (considering there isn’t any additional numbers in the argument of the sinusoidal). Every point on a sinusoidal function has a corresponding vector on the unit circle. 

### 1.1.1: What Does the Complex Exponential Represent?

As previously mentioned, the Fourier transform is used to uncover the periodic nature of continuous functions and discrete data sets. This is done by relying on the two fundamental periodic functions in mathematics, sin and cosine. Even though at first it appears that these functions are not present in the DFT, these functions are present in the complex exponential term. Eulers formula of complex exponentials states that $e^{i\theta} = \cos\theta + i\sin\theta$. Knowing this, we can see that these trigonometric functions are present in the DFT, with some rather complex arguments. These following sections will address each one of these and make sense of the larger argument in the complex exponential. 

### 1.1.2: What is $ω_0$?

$ω_0$ represents the base angular frequency of the data set, which sets the period of the first harmonic of this data set to repeat every N values. This is done by setting $ω_0=2π/N$, which will scale the length of one rotation within the complex unit circle to N radians. Basically, this variable is setting up the period of our sinusoidal function at its base frequency to the length of the vector being transformed. This indicates that for a vector to be to be accurately analyzed with a DFT, the data points need to differ by a common time interval.

### 1.1.3: What is $k$
k represents the harmonic of the base frequency that is currently being analyzed. A harmonic of a periodic function represents an integer multiple of its base frequency. For example, take the function f(x)=sin⁡〖(kx)〗. When k=1, this function will be in its first harmonic, and when k=2, this function will be in its second harmonic. Each harmonic has a frequency k times more frequent than the base frequency. In the DFT, k is represented by the index of the resultant vector we are calculating, meaning that every harmonic of the original base frequency up to k=N is tested to see which periodic function the vector fits the best. 

### 1.1.4: What is $N$
n represents the index of the input vector that is currently being analyzed. For each value in the input vector, the complex exponential (which can also be referred to as a phasor) rotates forward in time by one step. What is meant by “stepping forward in time” however? In the context of the DFT, to step forward in time means to move from the time that the previous data point was recorded at to the point in time where this data point is being recorded. The DFT does this by first assuming the 0th data point has been measured at t=0, and that each data point is an even amount of time apart. The value n will then rotate the complex exponential to the next integer multiple of kω_0 on the unit circle, representing the passage of time in the DFT.  Rotation on the complex unit circle is the same as moving forward on the X-axis of a real sinusoidal function, so this rotation can also be visualized as moving forward on a sinusoidal from one integer multiple of kω_0 to the next. 
2.1.3: What is n?
n represents the index of the input vector that is currently being analyzed. For each value in the input vector, the complex exponential (which can also be referred to as a phasor) rotates forward in time by one step. What is meant by “stepping forward in time” however? In the context of the DFT, to step forward in time means to move from the time that the previous data point was recorded at to the point in time where this data point is being recorded. The DFT does this by first assuming the 0th data point has been measured at t=0, and that each data point is an even amount of time apart. The value n will then rotate the complex exponential to the next integer multiple of kω_0 on the unit circle, representing the passage of time in the DFT.  Rotation on the complex unit circle is the same as moving forward on the X-axis of a real sinusoidal function, so this rotation can also be visualized as moving forward on a sinusoidal from one integer multiple of kω_0 to the next. 

## 1.2: How does this sum measure alignment with a periodic function? 
The goal of the DFT is to find a periodic function that represents the repetition of a significant value in the input data set. 

### 1.2.1: How does the DFT represent data points from the input vector?
Before multiplication, the complex exponential in the summation has a magnitude of 1. However, you may recognize that the product $x_n e^(-iω_0 nk)$ is similar to a way of representing complex numbers, $|z| e^iθ$. Basically, what the product is doing is creating vectors in the direction of where we are in the complex unit circle, with a magnitude of $x_n$. To picture this visually, think of a unit circle with evenly spaced vectors (with spacing determined by nk), and each vector varies in magnitude. 

### 1.2.2: understanding of how the complex exponential evolves as k grows.  
When $k=1$, the complex exponential will complete one rotation of the complex unit circle, but as k grows more rotations of the complex unit circle will be introduced. If we have a data set of size N=4, one rotation will be made to represent every value in the data set as a vector on the unit circle when k=1, but when k=2, two rotations will have to be made. This concept of increased rotation is key to finding a harmonic of the base frequency that accurately represents the input vector.

### 1.2.3: Vector Addition
When you add a vector, you are essentially creating a new vector that spans from the tail of the first vector to the head of the second vector when the two vectors are put head to tail. Because of this, the more aligned the vectors are in terms of directions, the larger their sum will be. This also means two equal vectors pointing in the opposite direction will cancel out. 

### 1.2.4: Adding it all together
Based on the last 3 sub-sections, we can envision that as we increase harmonics in the DFT, vectors will start to populate the complex unit circle at different angles. Most of the time, when summed up, these vectors will largely cancel each other out to produce a resulting vector with a small magnitude. However, if there is a case where there is an outlier value in the data set that repeats at a harmonic of the base angular frequency, this harmonic will have a vector that dominates in the summation of all the vectors present, leading to a larger value for the magnitude of the resulting vector. This is how the DFT finds a sinusoidal function representing the periodic repetition of a significant value in the data set. The less significant the difference between this periodic value and the other values, the harder it is for the DFT to isolate a harmonic representing this value's repetition. 

## Section Two: Introducing the Fast Fourier Transfrom
This initial matrix multiplication has an order notation of O(N^2), which is not favorable for larger data sets. We want to find an approach that will get this complexity as close to O(N) as possible. With big data transformation algorithms like this, a desirable approach is to “divide and conquer”. The issue now, however, is finding a way to divide up the input vector without losing the periodic nature of the data set. 


