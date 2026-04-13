#  Linear Regression Visualizer

A full-stack interactive visualizer for Linear Regression from scratch.

## Stack
- **Backend**: FastAPI + NumPy (pure math, no sklearn)
- **Frontend**: React + Vite + Recharts

## Features
- MSE cost function + gradient descent from scratch
- **Batch GD**, **SGD**, **Mini-Batch GD**
- Animated regression line updating live
- Cost vs iterations curve
- Learning rate comparison (slow / good / diverge)
- House Prices & Student Scores datasets
- Quick presets (slow / good / diverge)

## API Endpoints

| Method | Path | Description |
|--------|------|-------------|
| GET | `/api/datasets` | List available datasets |
| POST | `/api/train` | Train model, returns history |
| GET | `/api/compare-lr` | Compare 4 learning rates |
| GET | `/health` | Health check |

### Train request body
```json
{
  "dataset": "house_prices",
  "variant": "batch",
  "alpha": 0.05,
  "iterations": 100,
  "batch_size": 4
}
```

---

## Math

**Cost (MSE)**:
```
J(w,b) = (1/m) * Σ (ŷᵢ - yᵢ)²
```

**Gradient Descent Update**:
```
w := w - α * ∂J/∂w
b := b - α * ∂J/∂b
```

**Partial Derivatives**:
```
∂J/∂w = (2/m) * Σ (ŷᵢ - yᵢ) * xᵢ
∂J/∂b = (2/m) * Σ (ŷᵢ - yᵢ)
```

Features are **normalized** (zero-mean, unit-variance) before training for stable convergence.

---

## Project Structure
```
linear-regression-viz/
├── backend/
│   ├── main.py          # FastAPI app — all math here
│   └── requirements.txt
├── frontend/
│   ├── src/
│   │   ├── App.jsx
│   │   ├── components/
│   │   │   ├── ControlPanel.jsx
│   │   │   ├── RegressionPlot.jsx
│   │   │   ├── CostPlot.jsx
│   │   │   ├── LRComparison.jsx
│   │   │   └── AnimationBar.jsx
│   │   └── utils/api.js
│   ├── index.html
│   └── vite.config.js
└── README.md
```
