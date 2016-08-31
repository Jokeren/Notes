#The Big Data Challenges of Connectomics

##Source

Nature Neuroscience 17, 1448¨C1454 (2014)

http://www.nature.com/neuro/journal/v17/n11/nn.3837/metrics

##Problem
Connectomics is an nascent field of study, growing with the development of novel data, that derives new questions like how information is stored in the brain and how genetic and environmental interactions influence brain's structure. There is a considerable uncertainty about what could be learned from this data.

##Solution
The process of understanding brain's structure and its function:

1. Collecting microscopy images at nanometer level. Even a cerebral cortex of a small rodent could take more than 600 years.

2. Image alignment.

3. Reconstruct the image data by automatic segmentation.

4. Feature detection. 

5. Graph generation.

As far as I understand, the goal of the project is to automate the process of alignment, segmentation, and graph construction and provide a high-level connectomics structure for users.

##My Questions&Notes

1. Where do we need concurrent structures? If I understand right, the construction of graph only need concurrent insertion that could be ran in parallel without intervention between processes in many cases.

2. I submitted a result to the ISBI challenge last year in which I used a deep learning method to automate segmenation. 

3. A practical project that needs analyzing connectomics.

4. Why did not you use GPUs?