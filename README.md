# SF-Signal

A template project for developing, researching, and backtesting trading signals.

## Project Structure

```
sf-signal/
├── src/
│   ├── framework/
│   │   ├── ew_dash.py            # Equal-weight dashboard (do not edit)
│   │   ├── opt_dash.py           # Optimal portfolio dashboard (do not edit)
│   │   └── run_backtest.py       # Run the backtest (edit config only)
│   └── signal/
│       └── create_signal.py      # Your signal implementation (edit this)
├── data/
│   ├── signal.parquet            # Output: Your signal
│   └── weights.parquet           # Output: Backtest weights
└── README.md
```

## Workflow

### 1. **Implement Signal** (`create_signal.py`)
   - Customize date ranges, data columns, and calculation logic
   - Develop your signal logic
   - Save signal to `data/signal.parquet`

   ```bash
   uv run create_signal
   ```

### 2. **View Equal-Weight Performance** (`ew_dash.py`)
   - Compare your signal against an equal-weight baseline
   - Analyze signal characteristics
   - Visualize signal properties and performance

   ```bash
   uv run ew_dash
   ```

### 3. **Run Backtest** (`run_backtest.py`)
   - Run MVO-based backtest on your signal
   - Generates optimal portfolio weights
   - Saves results to `data/weights.parquet`

   ```bash
   uv run backtest
   ```

### 4. **View Optimized Performance** (`opt_dash.py`)
   - View optimized portfolio performance
   - Analyze backtest returns, drawdowns, and metrics
   - Compare with equal-weight baseline

   ```bash
   uv run opt_dash
   ```

## Data Files

All data files are stored in the `data/` directory:

- **`data/signal.parquet`**: Output from `create_signal.py`
  - Columns: `date`, `barrid`, `alpha` (your signal)
  - Format: Parquet (AlphaSchema)

- **`data/weights.parquet`**: Output from backtest
  - Contains: Portfolio weights and performance data
  - Format: Parquet

## Quick Start

```bash
# 1. Implement your signal
# Edit src/signal/create_signal.py with your logic
uv run create_signal

# 2. View equal-weight performance
uv run ew_dash

# 3. Run backtest
uv run backtest

# 4. View optimized performance
uv run opt_dash
```

## Template Files (Do Not Need to Edit)

The following files are templates and should not be modified:
- `src/framework/ew_dash.py` - Equal-weight comparison dashboard
- `src/framework/opt_dash.py` - Optimized portfolio dashboard
- `src/framework/run_backtest.py` - Backtest runner

**All signal customization happens in `src/signal/create_signal.py`.**

## Configuration

Update `src/framework/run_backtest.py` if needed:
- `byu_email`: Your BYU email for job submission
- `gamma`: Transaction costs or risk aversion parameter
- `constraints`: Add portfolio constraints
- `slurm`: Adjust computational resources

## Next Steps

1. Implement your signal logic in `src/signal/create_signal.py`
2. Run `uv run create_signal` to generate your signal
3. Compare against baseline with `uv run ew_dash`
4. Run backtest with `uv run backtest`
5. Analyze optimized results with `uv run opt_dash`
6. Iterate and refine your approach

---

**Note**: This is a template project. Customize `src/signal/create_signal.py` with your unique signal logic, then use the workflow above to research and backtest your ideas.
