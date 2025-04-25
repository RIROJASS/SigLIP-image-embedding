---

# 🏺 SigLIP-Image-Embedding

---
Multimodal search and benchmarking pipeline for a large dataset of pottery images using [SigLIP](https://arxiv.org/abs/2303.15343).  
This project allows for natural language queries like:

> “An image of a bird on pottery”  
> “Pottery with human figures”  
> “An image of a boat”

…and returns the most visually and semantically relevant matches from the dataset.

---

## 🔍 What This Repo Does

- Embeds 3,157 pottery images using **SigLIP**
- Stores embeddings in a **FAISS index** for fast vector search
- Allows **natural language queries** against visual features
- Benchmarks results against labeled image categories (`birds`, `boats`, `mammals`, `humans`)
- Calculates **precision & recall @ k**
- Includes **3D UMAP visualizations** using both Matplotlib and Plotly

---

## 📦 Dataset

The dataset consists of:

- 3,157 pottery images
- Manually curated benchmarks in four categories:
  - `boat`
  - `bird`
  - `mammal`
  - `human`
- Stored locally (not bundled in this repo)

---

## 🧠 Embedding Strategy

This project uses:

- **SigLIP models with patch size 16 and input resolutions of 224x224, 384x384, and 512x512**
- FAISS for indexing and retrieval
- Embeddings are extracted using `get_image_features()` for image search and `get_text_features()` for query matching
- All image embeddings are L2-normalized and stored in a **1024-dim FAISS index**

> ✅ Based on testing, **the so400m model at 384 resolution** strikes the best balance between precision, recall, and computational efficiency.

---

## 🧪 Query Testing + Metrics

- Example queries:  
  `"an image of a deer or mammal on a piece of pottery"`  
  `"an image of a boat"`  
  `"an image of a bird"`  
  `"an image of a human"`  

- Queries are evaluated by comparing returned images to benchmark categories using **Precision@10** and **Recall@10**.

### 📊 Results Summary

**so400m model @ 384 resolution**
| Category | Precision@10 | Recall@10 |
|----------|--------------|-----------|
| Boat     | 0.10         | 1.00      |
| Bird     | 1.00         | 0.37      |
| Human    | 0.10         | 0.06      |
| Mammal   | 0.30         | 0.38      |

---

## 📈 Visualizations

The repo supports:

- **Bar chart** plots of precision/recall per category
- **3D UMAP plots** of image embeddings
  - Matplotlib version (`umap_3d_plot.png`)
  - Interactive Plotly version (`umap_3d_interactive.html`)

> Each UMAP point can be explored with hover-to-preview, including image filename and truncated embedding values.

---

## 🗂️ File Structure

```
/notebooks
    SiglipIndexSearchScriptMuseumDataBase384.ipynb    # Core embedding + retrieval logic

/data
    MuseumData/                                       # Directory with .jpg/.JPG images
    Benchmarks/                                       # Folder with benchmark categories

/saved
    siglip_70k.index                                  # Serialized FAISS index
    umap_3d_plot.png                                  # Static visualization
    umap_3d_interactive.html                          # Interactive Plotly visualization
```

---

## 🚀 Getting Started

1. **Install dependencies**:
   ```bash
   pip install datasets faiss-gpu sentencepiece git+https://github.com/NielsRogge/transformers.git@add_siglip
   pip install umap-learn plotly bokeh
   ```

2. **Set up the project directory**:
   ```python
   project_path = '/your/path/to/project'
   os.chdir(project_path)
   ```

3. **Run the notebook**:
   Open `SiglipIndexSearchScriptMuseumDataBase384.ipynb` in Jupyter and follow the cells from top to bottom.

---

## 🤝 Contributing

Pull requests welcome. To contribute:

1. Fork the repo  
2. Create a feature branch  
3. Submit a PR with clear description of changes  

Ideas welcome for improvements to search, benchmarking, and visualization.

---

## 📄 License

MIT License  
See `LICENSE` file for details.

---

## ✉️ Contact

Maintainer: Raul Rojas
Email: raul.rojas@ufl.edu

---
