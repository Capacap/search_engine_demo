# Multimodal Search Engine

A bidirectional semantic search system that enables natural language image retrieval and image-to-text discovery using CLIP (Contrastive Language-Image Pre-training) embeddings.

## Architecture

This implementation demonstrates the mathematical elegance of multimodal semantic similarity through normalized vector embeddings projected onto a unit hypersphere, where cosine similarity reduces to efficient dot product operations.

### Core Components

- **Embedding Generation**: Projects images and text into a unified 512-dimensional semantic manifold using CLIP-ViT-Base-Patch32
- **Similarity Computation**: Leverages L2-normalized embeddings for O(n) cosine similarity via matrix operations
- **Deduplication Algorithm**: Ensures unique image results while preserving optimal semantic matches
- **Storage Architecture**: HDF5-based compressed storage with metadata preservation and integrity validation

## Features

### 🔍 Text → Image Search
Search through 8,091+ images using natural language queries. The system maps textual concepts to visual representations in embedding space.

### 🖼️ Image → Text Search  
Upload images to discover semantically similar captions from the dataset, enabling reverse semantic lookup.

### 🎨 Interactive Interface
Gradio-powered web interface with intuitive tabbed navigation, real-time results, and similarity scoring.

## Technical Specifications

- **Model**: OpenAI CLIP-ViT-Base-Patch32
- **Dataset**: Flickr8K (40,455 image-caption pairs)
- **Embedding Dimension**: 512
- **Storage Format**: HDF5 with gzip compression
- **Similarity Metric**: Cosine similarity (via normalized dot product)
- **Interface Framework**: Gradio

## Installation

```bash
# Clone repository
git clone <repository-url>
cd search_engine_demo

# Install dependencies
pip install -r requirements.txt

# Create data directory
mkdir -p data
```

## Usage

### 1. Data Preparation
```bash
jupyter notebook notebooks/part01_data_preparation.ipynb
```
Downloads Flickr8K dataset, generates CLIP embeddings, and stores them in compressed HDF5 format.

### 2. Search Functionality Testing
```bash
jupyter notebook notebooks/part02_search_functionality.ipynb
```
Demonstrates core search algorithms with comparative analysis of standard vs. diverse search variants.

### 3. Launch Web Interface
```bash
jupyter notebook notebooks/part03_multimodal_interface.ipynb
```
Launches the interactive Gradio interface for bidirectional semantic search.

## Mathematical Foundation

The system operates on the principle that semantic similarity can be expressed as geometric proximity in embedding space. By normalizing embeddings to unit vectors, cosine similarity becomes:

```
similarity(query, image) = query · image
```

This reduction enables efficient similarity computation across large datasets while maintaining semantic fidelity.

## Project Structure

```
search_engine_demo/
├── notebooks/
│   ├── part01_data_preparation.ipynb      # Dataset loading and embedding generation
│   ├── part02_search_functionality.ipynb  # Core search algorithms and testing
│   └── part03_multimodal_interface.ipynb  # Interactive web interface
├── data/
│   ├── flickr8k_embeddings.h5            # Compressed embeddings storage
│   └── datasets/
│       └── adityajn105/flickr8k/
│           ├── Images/                     # 8,091 JPEG images
│           └── captions.txt               # Image-caption mappings
├── requirements.txt                        # Python dependencies
└── README.md                              # Project documentation
```

## Performance Characteristics

- **Embedding Generation**: ~4.46 batches/second (batch_size=32)
- **Search Latency**: Sub-second response for datasets up to 40K+ items
- **Memory Efficiency**: Compressed storage reduces disk usage by ~60%
- **GPU Acceleration**: CUDA-optimized for NVIDIA hardware

## Dependencies

Key technical dependencies:
- `torch` - PyTorch deep learning framework
- `transformers` - Hugging Face model hub integration  
- `h5py` - HDF5 storage interface
- `gradio` - Web interface framework
- `numpy` - Vectorized operations
- `Pillow` - Image processing

## Academic Context

This implementation serves as a practical demonstration of:
- Cross-modal representation learning
- Semantic embedding space geometry
- Efficient similarity search algorithms
- Multimodal AI system architecture

The codebase exhibits production-ready patterns including comprehensive error handling, resource management, and immutable data design principles.

---

*Built with mathematical rigor and computational elegance.*
