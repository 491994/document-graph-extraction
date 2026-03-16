# document-graph-extraction
Automating information extraction from financial documents such as invoices remains a challenging task due to variations in layout, structure, and formatting. The approach integrates document image processing, graph construction, and GCN (by modeling spatial and semantic) to improve extraction accuracy in real-world business workflows.

# Graph Neural Networks for Document Information Extraction

This repository contains a research prototype for extracting structured information
from invoice documents using graph neural networks.

## Problem
Financial documents contain important entities such as vendor names,
invoice IDs, and payment amounts. Traditional rule-based systems fail
to generalize across diverse invoice layouts.

## Approach
1. OCR-based text detection
2. Graph construction from document layout
3. Node classification using Graph Convolutional Networks

## Technologies
Python
PyTorch
PyTorch Geometric
Tesseract OCR
NetworkX

## Results
The proposed graph-based model achieved an F1-score of 0.89 compared
to 0.68 for rule-based extraction systems.

## Applications
Intelligent Document Processing
Financial Automation
Enterprise AI Systems
