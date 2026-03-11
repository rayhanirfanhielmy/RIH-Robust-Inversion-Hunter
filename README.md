# RIH: Robust Inversion Hunter 🎯

**RIH (Robust Inversion Hunter)** is a fully automated, end-to-end computational framework designed to optimize the seismic moment tensor inversion process for local and regional earthquakes. 

Developed by **Rayhan Irfan Hielmy**, this tool integrates a Genetic Algorithm (GA) with the robust `mttime` inversion engine to eliminate the subjective and time-consuming manual trial-and-error process of seismic station selection.

## ✨ Key Features
* **One-Click Execution:** Bundled as a single executable (`RIH.run`), bypassing complex Linux dependency installations and environment setups.
* **Smart Station Selection:** Uses a Genetic Algorithm to automatically search for the optimal station sub-network that maximizes Variance Reduction (VR) and Double Couple (DC) percentages.
* **Lightweight & Fast:** Highly efficient architecture capable of finishing the entire inversion workflow (from raw data pre-processing to final GA selection) in **under 10 minutes** on a standard entry-level laptop (e.g., Intel Core i3, 4GB RAM).
* **Interactive GUI:** Easy-to-use dialog boxes for configuring velocity models, depth grids, and GA hyperparameters directly, without needing to edit command-line scripts.

## 📂 Directory Structure Requirements
Before running the application, ensure your working directory contains the necessary raw data structured as follows:

    Working_Directory/
    ├── RIH.run               # The main executable downloaded from Releases
    ├── datetime.csv          # Earthquake source parameters (origin time, lat, lon, depth)
    ├── data_stations/        # Folder containing station metadata respons (StationXML format)
    └── data_waveform/        # Folder containing raw broadband waveforms (.mseed)

## 🚀 Installation and Usage

**1. Download the Executable:**
Go to the [Releases](https://github.com/rayhanirfanhielmy/RIH-Robust-Inversion-Hunter/releases) page and download the latest `RIH.run` file.

**2. Prepare the Data:**
Place the downloaded `RIH.run` file into your working directory containing your earthquake data as shown in the structure above.

**3. Make it Executable:**
Open your Linux terminal, navigate to your working directory, and grant execution permissions:

    chmod +x RIH.run

**4. Run the Framework:**
Execute the program:

    ./RIH.run

**5. Follow the GUI Prompts:**
The interactive GUI will guide you to configure your inversion settings:
* Select your preferred Velocity Model (Default: `gil7.d`).
* Set the Depth Grid boundaries for the grid search.
* Configure the Waveform Filter (Freqmin/Freqmax) and Genetic Algorithm parameters (Target VR/DC, Population Size, Mutation Rate, etc.).

## 📊 Outputs
Once the optimization is complete, RIH will generate an `output/` folder containing:
* `evolution_vr_dc.png`: The evolutionary graph of the Genetic Algorithm.
* `waveform_preprocessing.png`: Traces of the pre-processed waveforms.
* Plot images of the best Moment Tensor inversion (Beachball map, waveform fits, variance vs. depth).
* `timing_report.csv`: Execution time report for each computational stage.
* The final optimized `mtinv.in` configuration file.
