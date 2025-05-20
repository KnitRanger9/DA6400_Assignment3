# DA6400_Assignment3

Roll: DA624M004

Link to wandb: https://wandb.ai/da24m004-iitmaana/hindi-transliteration_3/reports/DA6401-Assignment-3--VmlldzoxMjg1NzUwMw?accessToken=qc9sgln1dthiylimg5ziuhxmmwrm1tbpkhdbglo4vzczxo450xcs7d5woaorqlac

## Instructions on running code:
- Upload the .ipynb file to kaggle
- Use ctrl+f to find and replace the wandb api keys in `wandb.login(key="<your key>")`
- Run all the cells

## Assignment Overview

This Python project implements a sequence-to-sequence model with attention mechanism for Hindi transliteration, converting romanized Hindi text to native Devanagari script. The project focuses heavily on model interpretability through advanced attention visualization techniques.

## Project Structure

The project consists of the following key components:

1. **Model Implementation**
   - Encoder-Decoder architecture with attention mechanism
   - LSTM-based sequence processing
   - Beam search decoding capabilities

2. **Visualization Modules**
   - Static attention heatmaps
   - Interactive attention visualization
   - Connectivity diagrams for input-output relationships

3. **Evaluation Framework**
   - Character and word accuracy metrics
   - Integration with Weights & Biases for experiment tracking
   - Hyperparameter management

## Key Functionality

### Attention Visualization Functions

#### `save_attention_visualization(model, dataloader, output_vocab, num_samples=5, save_path='attention_visualization.png')`
Creates comprehensive visualizations showing attention patterns:
- Generates heatmaps displaying attention weights between input and output characters
- Creates side-by-side visualization with connectivity diagrams
- Color-codes predictions to indicate correctness
- Saves results to specified path and logs to Weights & Biases

#### `interactive_attention_visualization(model, dataloader, output_vocab, index=0)`
Provides step-by-step animated visualization of the attention process:
- Shows progressive character generation
- Highlights input text based on attention weights
- Uses color gradients to represent attention intensity
- Returns predicted text and attention weights for further analysis

#### `generate_attention_connectivity_visualization(predictions, targets, inputs, attentions, n_samples=5)`
Creates diagrams showing relationships between input and output characters:
- Visualizes connections with line thickness representing attention strength
- Maps character positions with visual connections
- Color-codes outputs based on prediction accuracy
- Logs visualizations to Weights & Biases

### Evaluation Functions

#### `evaluate_attention_model_with_visualization()`
Comprehensive evaluation function that:
- Initializes Weights & Biases for experiment tracking
- Downloads and prepares Hindi transliteration dataset
- Creates vocabularies and dataloaders
- Tests the model and logs accuracy metrics
- Generates and logs various attention visualizations

#### `evaluate_with_config()`
Similar to the above but designed to work with wandb sweeps:
- Uses configuration from Weights & Biases sweep
- Allows for hyperparameter optimization
- Maintains consistent visualization capabilities

#### `run_interactive_visualization()`
Focused function for generating interactive visualizations:
- Loads model and test data
- Selects random examples to visualize
- Provides detailed step-by-step attention analysis
- Saves static visualizations of complete attention maps

## Technical Details

### Model Architecture
- **Encoder**: Processes input romanized text
- **Attention Decoder**: Generates Devanagari output with attention mechanism
- **Parameters**:
  - Embedding size: 64
  - Hidden size: 512
  - Number of layers: 2
  - Dropout: 0.2
  - Cell type: LSTM
  - Beam size: 3

### Visualization Techniques
- Heatmaps for displaying attention weight matrices
- Connectivity diagrams with weighted lines
- Color gradients to represent attention intensity
- Character-by-character highlighting for interactive analysis

### Font Handling
Custom handling for Devanagari font rendering:
- Downloads and installs Noto Sans Devanagari font
- Registers the font with matplotlib
- Creates custom FontProperties for consistent rendering

**Conclusion**: This project demonstrates both the power of attention-based neural machine translation and the importance of model interpretability through visualization techniques.
