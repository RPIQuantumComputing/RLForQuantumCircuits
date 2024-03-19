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
