# turbo_vec_stresstesting


## Update my CV like CJ Cassar
   https://www.cjmcassar.com/


## Meetup of Qdrant and how to explain the algorithm of TurboQdrant Lloyd-Max 
   Achieving Production-Quality with TurboQdrant Lloyd-Max, renormalization and 1-bit       asymmetric scoring from RaBitQ. 


## Metrics of Performance: 
   Compression Ratio (Storage Space gained) --> Lower Inference Time vs
   Quality (Recall Tradeoffs) 
   Recall@1
   Recall@2
   Recall@5
   Recall@10
   Recall@20


## Turbquant? 
   What is TurboQuant? 

## Why would you use it ? 
   Well when you compare this algorithm against the previous FAISS algorithm you know that its better. You have "more or less" the same Recall performane as FAISS but none of the drawback 

## How does Turboquant compare to the other prevous algorithms? 
   Which algorithms existed in the past? 
   We had: HNSW, IVFlat Index

   how does turboquant compare to HNWSW and IV Flat Index??
   <Compare and Contrast those studies here and see what happens>

## Implementation Guidelines
   Before writing the code, keep the geometric pipeline in mind: 
   [Input Vector x] ──> [Extract L2 Norm] ──> [Unit Vector x_hat] ──> [Apply Random     Rotation (Hadamard/Dense)] ──> [Scalar Lloyd-Max Binning]
   
## The Architecture of Stage 1:
   1. Extract the Magnitude (L2 Norm): We pull out the absolute scale of the vector and save it as a high-precision float (f16 or f32). This means the remaining vector has a norm of exactly 1.0.

   2. Random Rotation (II): Multiplying our unit vector by a random orthogonal matrix distributed over the hypersphere smashes any outlier spikes. The individual coordinates flatten out into a highly predictable, conventrated Beta Distribution (which behaves identically to a standard Gaussian in high dimensions).

   3. Lloyd-Max Scalar Quantization: Because the distribution of coordinates is now fixed and independent, we map each coordinate to its closest centroid in a pre-computed Lloyd-Max codebook.
   

## Add a page for subvector and strategy Product Quantisation 
    Links and implementation for product quantisation
