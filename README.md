# Multimodal Search Engine

A semantic search system that enables bidirectional search between images and text using CLIP embeddings. Users can search for images using natural language descriptions or find similar text captions by uploading images.

## Overview

This project implements a multimodal search engine using OpenAI's CLIP model to create vector embeddings for both images and text. The system uses cosine similarity to find semantically related content across modalities.

### Key Components

- **Data Processing**: Loads and validates the Flickr8K dataset, generating normalized embeddings for all images and captions
- **Search Engine**: Implements efficient similarity search using dot product operations on normalized embeddings  
- **Web Interface**: Provides an interactive Gradio-based interface for both text-to-image and image-to-text search
- **Storage**: Uses compressed HDF5 format for efficient storage and retrieval of embeddings

## Features

### Text to Image Search
Find images that match natural language descriptions. The system searches through 8,091 images from the Flickr8K dataset.

### Image to Text Search  
Upload an image to find semantically similar text descriptions from the dataset.

### Interactive Web Interface
Browser-based interface with separate tabs for each search mode, configurable result counts, and detailed similarity scores.

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
Downloads Flickr8K dataset, generates CLIP embeddings, and stores them in HDF5 format.

### 2. Search Functionality Testing
```bash
jupyter notebook notebooks/part02_search_functionality.ipynb
```
Demonstrates the search algorithms and compares different result filtering approaches.

### 3. Launch Web Interface
```bash
jupyter notebook notebooks/part03_multimodal_interface.ipynb
```
Launches the interactive web interface for searching images and text.

## Technical Details

The search algorithm uses L2-normalized CLIP embeddings, allowing cosine similarity to be computed efficiently as a dot product:

```
similarity(query, target) = normalized_query · normalized_target
```

This approach scales well to large datasets while maintaining semantic accuracy.

## Project Structure

```
search_engine_demo/
├── notebooks/
│   ├── part01_data_preparation.ipynb      # Dataset loading and embedding generation
│   ├── part02_search_functionality.ipynb  # Search algorithm implementation and testing
│   └── part03_multimodal_interface.ipynb  # Web interface
├── data/
│   ├── flickr8k_embeddings.h5            # Stored embeddings
│   └── datasets/
│       └── adityajn105/flickr8k/
│           ├── Images/                     # Dataset images
│           └── captions.txt               # Image captions
├── requirements.txt                        # Python dependencies
└── README.md                              # Documentation
```

## Performance

- **Embedding Generation**: ~4.46 batches/second (RTX 3060 Ti, batch_size=32)
- **Search Speed**: Sub-second response for 40K+ embeddings
- **Storage**: HDF5 compression reduces storage by ~60%
- **Requirements**: CUDA-compatible GPU recommended

## Dependencies

Core libraries:
- `torch` - PyTorch framework
- `transformers` - Hugging Face transformers library
- `h5py` - HDF5 file handling
- `gradio` - Web interface
- `numpy` - Array operations
- `Pillow` - Image processing

See `requirements.txt` for complete dependency list with versions.

## Implementation Notes

This project demonstrates practical implementation of:
- Cross-modal embedding alignment using CLIP
- Efficient similarity search with normalized vectors
- Interactive multimodal interfaces
- Compressed storage for large embedding datasets

The implementation includes error handling, input validation, and modular design for easy extension and modification.