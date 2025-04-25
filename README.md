# SigLIP-image-embedding

Code from a recent project. Taken from jupyter notebooks.

# Basic Workflow
Receives images from a dataset as input, embeds them with metadata using automatic image analysis, and allows for image retrieval using natural language searching

## Data Processing
The code takes 3157 images as input. From them I manually categorized the images into 4 benchmarks to be used for grounding the model.
1. boat
2. birds
3. mammals
4. humans

## Data Analysis
The results of the grounding are visualized via precision & recall @ k metrics (i.e. for however many images were in the output, how many match the benchmark images in:
1. images that match benchmark/total images in output
2. images that match benchmarks/total images in benchmark)
