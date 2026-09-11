# Models Directory

This directory contains trained PCB defect detection models **downloaded from Kaggle**.

## ⚠️ IMPORTANT: You must train and download models first!

### Step 1: Train on Kaggle
Follow the main README instructions to train your model on Kaggle.

### Step 2: Download Models from Kaggle
After training completes, use this code in your Kaggle notebook:

```python
import zipfile
from IPython.display import FileLink

with zipfile.ZipFile('/kaggle/working/pcb_models.zip', 'w') as zipf:
    zipf.write('/kaggle/working/pcb_model.pt', 'pcb_model.pt')          # Compatibility
    zipf.write('/kaggle/working/pcb_model.onnx', 'pcb_model.onnx')      # Best performance

FileLink('/kaggle/working/pcb_models.zip')
```

### Step 3: Place Models Here
Extract the downloaded zip and place the files in this directory:

```
models/
├── pcb_model.onnx    # 🚀 BEST performance (~8ms) - GUI will use this
├── pcb_model.pt      # ⚡ Compatibility fallback (~15ms)
└── README.md         # This file
```

## Model Performance

| Format | File | Speed | Usage |
|--------|------|-------|-------|
| 🚀 **ONNX** | `pcb_model.onnx` | ~8ms | **GUI automatically selects this** |
| ⚡ PyTorch | `pcb_model.pt` | ~15ms | Compatibility fallback |

## Usage with GUI

1. Place both model files in this directory
2. Launch the GUI: `python -m gui_test.app`
3. The GUI will **automatically detect and load the ONNX model** for best performance
4. If ONNX is not available, it will use the PyTorch model

## File Structure After Setup

```
models/
├── pcb_model.onnx    # Downloaded from Kaggle
├── pcb_model.pt      # Downloaded from Kaggle
└── README.md
```

The GUI test interface will automatically find and use these models!