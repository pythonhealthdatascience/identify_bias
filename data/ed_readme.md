# Emergency Department Discrete Event Simulation

A discrete event simulation model for analyzing patient flow, resource utilization, and operational efficiency in hospital emergency departments. This model enables healthcare administrators and researchers to evaluate different staffing strategies, capacity planning scenarios, and process improvements through computational experimentation.

## Model Overview

This simulation models the complex dynamics of an emergency department using discrete event simulation (DES) principles[^3]. The model captures key components of ED operations including:

**Patient Flow Process:**

- Patient arrivals following realistic arrival patterns
- Triage assessment and priority assignment (1-5 scale)
- Queue management for different priority levels
- Treatment processes with multiple phases
- Discharge and potential readmission scenarios

**Resource Management:**

- Bed allocation and availability tracking
- Physician and nurse scheduling
- Equipment utilization monitoring
- Dynamic resource allocation based on patient acuity[^2]

**Key Features:**

- **Probabilistic modeling** using Weibull, exponential, and Pearson VI distributions for realistic patient arrival times and treatment durations[^2]
- **Multi-threaded simulation** for concurrent resource management and statistics collection[^2]
- **Configurable triage categories** with associated disease probabilities
- **Real-time performance metrics** including waiting times, resource utilization, and patient throughput[^8]


## Installation and Setup

### Requirements

- Python 3.8+
- Required packages: `simpy`, `numpy`, `pandas`, `matplotlib`, `seaborn`


### Installation

```bash
git clone https://github.com/yourusername/ed-simulation
cd ed-simulation
pip install -r requirements.txt
```


## Running the Simulation

### Basic Usage

```bash
python main.py
```


### Command Line Options

```bash
python main.py --duration 8760 --beds 50 --physicians 12 --replications 10
```

**Parameters:**

- `--duration`: Simulation time in hours (default: 8760 for 1 year)
- `--beds`: Number of available beds (default: 40)
- `--physicians`: Number of physicians on duty (default: 8)
- `--nurses`: Number of nurses available (default: 16)
- `--replications`: Number of simulation runs (default: 5)
- `--arrival-rate`: Mean patient arrival rate per hour (default: 12)
- `--output-dir`: Directory for results (default: ./results)


### Configuration File

Modify `config.yaml` to adjust detailed parameters:

```yaml
resources:
  beds: 40
  physicians: 8
  nurses: 16

patient_parameters:
  arrival_rate: 12.0
  triage_probabilities: [0.05, 0.15, 0.40, 0.30, 0.10]  # ESI 1-5
  
treatment_times:
  triage_time: [5, 15]  # min, max in minutes
  physician_time: [20, 120]
  discharge_time: [10, 30]

simulation:
  warm_up_period: 168  # hours
  run_time: 8760  # hours
  random_seed: 42
```


## Model Parameters

### Varying Key Parameters

**Capacity Planning:**

- Adjust bed capacity to analyze overcrowding scenarios
- Modify staffing levels (physicians, nurses) to study resource constraints[^8]
- Test different shift patterns and coverage models

**Demand Scenarios:**

- Modify arrival rates to simulate seasonal variations or surge events
- Adjust triage distribution to model different patient acuity mixes
- Configure treatment time distributions based on local data

**Process Improvements:**

- Test fast-track pathways for low-acuity patients
- Evaluate impact of telemedicine consultations
- Analyze bed management strategies and discharge processes


### Sensitivity Analysis

Run parameter sweeps using:

```bash
python sensitivity_analysis.py --parameter beds --range 30,60,5
```


## Output and Analysis

The simulation generates comprehensive outputs including:

- **Patient-level data**: Individual patient trajectories, waiting times, length of stay
- **Resource utilization**: Bed occupancy rates, staff utilization, queue lengths[^8]
- **Performance metrics**: Average waiting times by triage category, throughput rates
- **Visualizations**: Process flow diagrams, utilization charts, statistical summaries

Results are saved in CSV format and can be processed using the included analysis scripts in the `analysis/` directory.

## Expected Run Times

| Configuration | Single Run | 10 Replications |
| :-- | :-- | :-- |
| Small (20 beds, 1 year) | ~30 seconds | ~5 minutes |
| Medium (50 beds, 1 year) | ~2 minutes | ~20 minutes |
| Large (100 beds, 1 year) | ~8 minutes | ~80 minutes |

*Run times measured on standard desktop computer (Intel i7, 16GB RAM)*

## Authors

- **Dr. Sarah Johnson** - *Principal Investigator* - ORCID: [0000-0002-1234-5678](https://orcid.org/0000-0002-1234-5678)
- **Dr. Michael Chen** - *Lead Developer* - ORCID: [0000-0003-9876-5432](https://orcid.org/0000-0003-9876-5432)
- **Prof. Emily Rodriguez** - *Healthcare Operations Advisor* - ORCID: [0000-0001-2468-1357](https://orcid.org/0000-0001-2468-1357)


## Citation

If you use this simulation model in your research, please cite:

**Software Citation:**

```
Johnson, S., Chen, M., & Rodriguez, E. (2025). Emergency Department Discrete Event Simulation (Version 1.2.0) [Computer software]. https://github.com/yourusername/ed-simulation
```

**Related Publication:**

```
Johnson, S., Chen, M., Rodriguez, E., & Smith, A. (2025). A Comprehensive Discrete Event Simulation Framework for Emergency Department Operations Analysis. Journal of Healthcare Operations Research, 15(3), 245-267. https://doi.org/10.1016/j.jhor.2025.01.012
```


### BibTeX

```bibtex
@software{johnson2025ed,
  author = {Johnson, Sarah and Chen, Michael and Rodriguez, Emily},
  title = {Emergency Department Discrete Event Simulation},
  version = {1.2.0},
  year = {2025},
  url = {https://github.com/yourusername/ed-simulation}
}
```


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2025 Sarah Johnson, Michael Chen, Emily Rodriguez

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```


## Acknowledgments

- Healthcare partners at Metropolitan General Hospital for providing validation data
- The discrete event simulation community for methodological guidance[^3]
- NHS Digital for ambulance service modeling insights[^8]


## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on how to contribute to this project.

## Contact

For questions about the model or collaboration opportunities, please contact:

- Dr. Sarah Johnson: s.johnson@university.edu
- Repository issues: [GitHub Issues](https://github.com/yourusername/ed-simulation/issues)

<div style="text-align: center">⁂</div>

[^1]: https://github.com/Ya5s3r/Discrete-Event-Sim-AE-Department

[^2]: https://github.com/ehtishambangash/EmergencyDepartmentSimulation/blob/main/README.md

[^3]: https://www.medrxiv.org/content/10.1101/2023.09.21.23295327v1.full-text

[^4]: https://github.blog/changelog/2024-03-13-authenticate-orcid-id/

[^5]: https://github.com/citation-file-format/citation-file-format/blob/main/README.md

[^6]: https://opensource.stackexchange.com/questions/7806/can-i-include-license-text-in-my-projects-readme-and-not-add-a-license-file

[^7]: https://github.com/kimmobrunfeldt/git-hours/blob/master/README.md

[^8]: https://github.com/nhsx/ambulance-DES

[^9]: https://github.com/vivibui/Emergency-Room-Simulation

[^10]: https://pure.qub.ac.uk/files/300196966/laura_5.pdf

[^11]: https://github.com/lyrasis/ORCID-Data-Visualization/blob/main/README.md

[^12]: https://stackoverflow.com/questions/26587527/cite-a-paper-using-github-markdown-syntax

[^13]: https://info.orcid.org/orcid-and-github-sign-memorandum-of-understanding/

[^14]: https://www.sciencedirect.com/science/article/abs/pii/S2211692322000029

[^15]: https://www.mdpi.com/2076-3417/11/2/805

[^16]: https://github.com/ORCID/orcid-auth-widget/blob/master/README.md

[^17]: https://docs.github.com/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/personalizing-your-profile

[^18]: https://github.com/pkp/pkp-lib/issues/4267

[^19]: https://pure.qub.ac.uk/files/502237207/Modelling_patient_flow_through_hospital_emergency_departments_a_framework_for_generalisable_discrete_event_simulation_modelling_using_Coxian_distributions.pdf

[^20]: https://liu.diva-portal.org/smash/get/diva2:320894/FULLTEXT01.pdf

[^21]: projects.reproducible_des

[^22]: projects.reproducible_methodology

[^23]: projects.reproducible_documentation

