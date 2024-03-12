# FFT Tensor Decomposition

**What is the FFT Algorithm and how will we represent it?** 
The input to the Fast Fourier Transform (FFT) algorithm is often a $1 * N$ dimensional vector representing a signal sampled over time. It builds off the Discrete Fourier Transform, which multiplies the input vector by a $NxN$, by taking a divide and conquer approach.
>FFT Recurrence: $T(n) = 2T(n/2) + O(n)$
>FFT Runtime: $O(nlogn)$

We will represent the FFT as a tensor of $Rank = 3$ containing $1 x N$ input vectors in order for the RL agent to look for shortcuts in the tensor, therby reducing memory consumption and runtime. 
**![](https://lh7-us.googleusercontent.com/-5F6rZEeSPCnC6IxT-miAjgmwz5SjGPB8MRXrrGmhaJaTKJuzTf_LMtFZJjegPRIkhWWtwXvdiF9NKl70O72C5pa_aIwiS2lxeieyDZBuAYSPwufjSaNKBguO7snuvKPzUwGBdUyCcN9Wxgg7xPdRGbMdg=s2048)**
**How can reinforcement learning be used to optimize the FFT Algorithm?**
Reinforcement learning are able to take a heuristic approach to problem solving, similar to humans. The main difference is that computers can process many times more data and operations than the human brain can. This allows the model to try many different methods for solving a problem and with each mistake or success, it adapts and follows the path that will maximize the amount of reward it will gain.
>Note: The reward is determined by a function that calculates how favorable a state or decision is. The sum of these rewards over a set of actions is the return.

Our RL algorithm will search through the tensor and try different approaches of performing the FFT while comparing the results to the actual output. Given the right environment and learning functions the algorithm can arrive at new and interesting results.

Sources: Steven L. Brunton; Professor,  [University of Washington](https://scholar.google.com/citations?view_op=view_org&hl=en&org=5340226318625937772)