# VC Fund Simulation Notebook

This repository contains a Google Colab notebook designed to simulate venture capital fund performance based on various assumptions and compare the outcomes. This tool allows users to experiment with different investment strategies, probabilities of success, and exit multiples to understand their potential impact on fund metrics like MOIC, TVPI, and IRR.

## Project Structure

*   `VC_Fund_Simulation.ipynb`: The main Google Colab notebook containing the simulation code, analysis, and visualizations.
*   `assumptions/`: Folder to store JSON files defining simulation parameters.
    *   `assumptions/default_assumptions.json`: An example assumption file.
*   `results/`: Folder where simulation outputs (detailed company data and fund metrics) are saved as CSV files.

## Getting Started

To use this notebook, you can open it directly in Google Colab:

1.  Click on the `VC_Fund_Simulation.ipynb` file in the GitHub repository.
2.  Click the "Open in Colab" button at the top of the notebook view.

Alternatively, you can clone this repository to your local machine and open the notebook in a Jupyter environment.

## How to Use the Notebook

The notebook is structured into several sections:

1.  **Import Libraries:** Imports necessary Python libraries.
2.  **Math Functions:** Includes the `irr` function for Internal Rate of Return calculation.
3.  **Assumptions Management:**
    *   Creates the `assumptions/` and `results/` folders.
    *   Generates a `default_assumptions.json` file in the `assumptions/` folder.
    *   Provides an interactive widget to select JSON assumption files from the `assumptions/` folder to use in the simulation.
    *   **Before running the simulations, you need to create or modify JSON files in the `assumptions/` folder with your desired parameters and select them using the widget.**
4.  **Simulation Functions:** Contains the core logic for running a single simulation run (`simulate_once`).
5.  **Run Simulations:**
    *   Loads the selected assumption files.
    *   Runs the simulation `NUM_SIMS` times for each assumption set.
    *   Saves detailed company-level results and fund-level metrics to CSV files in the `results/` folder.
    *   Prints a summary of mean metrics (MOIC, TVPI, IRR) across runs for each assumption file.
6.  **Visualization:** Generates plots to compare simulation outcomes across different assumption files, including:
    *   Breakdown of Companies by Stage
    *   Total Exit Proceeds by Stage
    *   Average Exit Proceeds per Simulation by Stage
7.  **Extra Cells (Appendix):** Additional cells for debugging or exploring individual simulation runs.

**Follow the instructions within the notebook cells sequentially.**

## Assumptions

Simulation parameters are defined in JSON files located in the `assumptions/` folder. The `default_assumptions.json` provides a template. Key parameters include:

*   `FUND_COMMITTED`: Total committed capital.
*   `INVESTABLE_CAPITAL`: Capital available for investment after fees.
*   `INIT_RESERVES`: Initial capital held in reserve.
*   `AVG_SEED_CHECK`: Average initial investment at the Seed stage.
*   `OWNERSHIP_SEED`: Initial ownership percentage acquired at Seed.
*   `PROB`: Probabilities of transitioning between stages (Seed to A, A to B, A to Exit, etc.).
*   `DILUTION`: Dilution percentages at each funding round (A, B, C).
*   `MULT`: Valuation multiples between stages and for exits.
*   `YEARS`: Time elapsed between stages.
*   `NUM_SIMS`: The number of simulation runs per assumption set.
*   `STRATEGY`: Follow-on investment strategy ("pro_rata" or "top_up").
*   `RNG_SEED`: Random number generator seed for reproducibility.

## Results

The simulation generates two types of CSV files in the `results/` folder for each assumption set:

*   `simulation_results_[assumption_file_name].csv`: Contains detailed data for each simulated company across all runs.
*   `fund_metrics_[assumption_file_name].csv`: Contains fund-level metrics (MOIC, TVPI, IRR) for each individual simulation run.

The notebook also displays a summary DataFrame (`results_summary_df`) with the mean and standard deviation of the key fund metrics across simulation runs for each assumption file.
