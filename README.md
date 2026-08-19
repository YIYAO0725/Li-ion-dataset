# Li-ion-database
Li-ion-dataset from online search
在网上找到的各种锂离子数据

# Battery Research Abbreviation Glossary

A full bilingual glossary for battery cycling, aging experiments, dataset classification, electrochemistry and battery ML research\. Suitable for GitHub dataset documentation\.

---

## 1\. Battery State Parameters 电池状态参数

|Abbreviation|Full Name|中文释义|Simple Explanation|
|---|---|---|---|
|**SOC**|State of Charge|荷电状态 / 剩余电量|Battery remaining capacity percentage \(0%–100%\), like a fuel gauge\.|
|**SOH**|State of Health|电池健康度|Battery aging index: current maximum capacity / original new capacity\.**80% SOH = EOL** for most lithium\-ion cells\.|
|**RUL**|Remaining Useful Life|剩余使用寿命|Remaining cycles before the battery reaches its end\-of\-life \(80% SOH\)\. Core ML prediction target\.|
|**EOL**|End of Life|寿命终止|Battery retirement threshold: capacity fades to 80% of initial capacity\.|
|**BOL**|Beginning of Life|全新初始状态|Brand\-new battery state with zero aging and degradation\.|
|**DOD**|Depth of Discharge|放电深度|Percentage of capacity discharged in one cycle; high DOD accelerates aging\.|
|**SOP**|State of Power|功率状态|Instant maximum output power, strongly affected by internal resistance aging\.|

---

## 2\. Cycling \& RPT Experimental Terms 循环与测试术语

|Abbreviation|Full Name|中文释义|Simple Explanation|
|---|---|---|---|
|**RPT**|Reference Performance Test|基准性能点检|Periodic battery health check during aging cycles\. Provides **ground\-truth capacity/SOH labels** for supervised ML\.|
|**HPPC**|Hybrid Pulse Power Characteristic|脉冲功率测试|Short current pulse test at different SOC levels to calculate DC internal resistance\.|
|**DCIR**|Direct Current Internal Resistance|直流内阻|Key aging feature; rises continuously during battery degradation\.|
|**CC**|Constant Current|恒流|Fixed current charging/discharging mode\.|
|**CV**|Constant Voltage|恒压|Fixed voltage charging stage for full saturation\.|
|**CC\-CV**|Constant Current Constant Voltage|恒流恒压充电|Standard lithium\-ion charging protocol\.|
|**OCV**|Open Circuit Voltage|开路电压|Steady voltage without current load, used for SOC calibration and hysteresis analysis\.|
|**EIS**|Electrochemical Impedance Spectroscopy|电化学阻抗谱|Precise impedance test to analyze SEI, charge transfer and electrolyte aging\.|

---

## 3\. Battery Material \& Chemistry 电池材料体系

|Abbreviation|Full Name|中文释义|Simple Explanation|
|---|---|---|---|
|**LFP**|Lithium Iron Phosphate|磷酸铁锂|Long cycle life, high safety, low energy density\.|
|**NMC**|Nickel Manganese Cobalt Oxide|三元锂|High energy density, mainstream EV cathode material\.|
|**LCO**|Lithium Cobalt Oxide|钴酸锂|Used in consumer electronics, high energy density but poor cycle life\.|
|**NCA**|Nickel Cobalt Aluminum Oxide|镍钴铝|High\-nickel high\-energy cathode material\.|
|**SEI**|Solid Electrolyte Interphase|固体电解质界面膜|Key aging mechanism: continuous SEI growth causes capacity loss\.|

---

## 4\. Dataset \& Machine Learning Terms 数据集与建模术语

|Term|Explanation \(English\)|中文释义|
|---|---|---|
|**Raw Data**|Direct instrument\-recorded time\-series data without manual calculation or fitting\.|仪器原始数据，未拟合、未二次处理|
|**Labeled Data**|Contains raw cycling features \(X\) \+ RPT\-measured ground\-truth SOH/capacity labels \(Y\), supports supervised learning\.|带标签数据：有RPT真值，可做SOH/RUL监督预测|
|**Unlabeled Data**|Only time\-series operating data, no periodic RPT ground\-truth aging labels\.|无标签数据：无RPT真值，仅适合无监督学习|
|**CLO**|Closed\-Loop Optimization, Bayesian auto\-optimization for fast charging protocols\.|闭环优化，快充策略自动迭代实验框架|
|**XFC**|Extreme Fast Charging, 10\-minute rapid charging strategy\.|极速快充|
|**BMS**|Battery Management System, monitors voltage, current, temperature and estimates SOC/SOH\.|电池管理系统|

---



# 电池数据集分类汇总（按一级分类）

## 1. Battery Aging and Degradation

### LFP (LiFePO₄ 磷酸铁锂)

| Dataset | Description | Task | Data Labeled or Not | Paper | Code |
| --- | --- | --- | --- | --- | --- |
| [MATR(LFP)](https://data.matr.io/1/projects/5c48dd2bc625d700019f3204) | consists of 124 commercial lithium-ion batteries cycled to failure under fast-charging conditions | RUL Prediction, SOH Estimation | ✅ SOC labels| [Data-driven prediction of battery cycle life before capacity degradation](https://www.nature.com/articles/s41560-019-0356-8) | [[Github 4]](https://github.com/rdbraatz/data-driven-prediction-of-battery-cycle-life-before-capacity-degradation) |
| [The Dataset for: Real-time personalized health status prediction of lithium-ion batteries using deep transfer learning(LFP)](https://data.mendeley.com/datasets/nsc7hnsg4s/2) | A dataset with 77 LFP/graphite cells (1.1 Ah nominal capacity and 3.3 V nominal voltage). The cells were cycled with an identical charge protocol but different multi-stage discharge protocols at a constant temperature of 30°C. | Real-time Personalized Health Status Prediction | ✅ discharge capacity, internal resistance labels| [Real-time personalized health status prediction of lithium-ion batteries using deep transfer learning](https://pubs.rsc.org/ee/article/15/10/4083/767199/Real-time-personalized-health-status-prediction-of) | [[Github 17]](https://doi.org/10.5281/zenodo.6827566) |
| [Naumann et al, 2021 (LFP-Gr)](https://data.mendeley.com/datasets/kxh42bfgtj/1) | Comprehensive calendar+cycle aging. Cell: Sony/Murata US26650-FTC1; Format: Cylindrical; Batteries: 114; Measurements: Charge-discharge, pulses, only summary data | Comprehensive calendar+cycle aging | ✅ capacity loss and resistance increase | [Analysis and modeling of calendar aging of a commercial LiFePO₄/graphite cell](https://www.sciencedirect.com/science/article/pii/S0378775319316593) | |
| [Ramirez-Meyers et al, 2023 (LFP-Gr)](https://data.mendeley.com/datasets/c7jhyd9c5t/1) | EIS. Cell: A123 (LithiumWerks) APR18650M1A APR18650M1B; Format: Cylindrical; Batteries: 422; Measurements: Charge-discharge, EIS | EIS | ✅ Capacity Labeled | [A statistical assessment of the state-of-health of LiFePO₄ cells harvested from a hybrid-electric vehicle battery pack](https://www.sciencedirect.com/science/article/pii/S2352152X22024616) | |
| [Attia et al, 2020 (LFP-Gr)](https://data.matr.io/1/projects/5d80e633f405260001c0b60a) | Cycle aging. Cell: A123 (LithiumWerks) APR18650M1A; Format: Cylindrical; Batteries: 240 | Cycle aging | ✅ used CLO training batches  | [Closed-loop optimization of fast-charging protocols for batteries with machine learning](https://www.nature.com/articles/s41586-020-1994-5) | |
| [Vilsen & Stroe, 2024 (LFP-Gr)](https://data.mendeley.com/datasets/yz4pttm73n/2) | Cycle aging. Format: Prismatic; Batteries: 3 | Cycle aging | ✅ RPT labels | [Dataset of lithium-ion battery degradation based on a forklift mission profile for state-of-health estimation and lifetime prediction](https://www.sciencedirect.com/science/article/pii/S2352340923009228)| |
| [Nowacki et al, 2025 (LFP-Gr)](https://digitalcommons.lib.uconn.edu/reil_datasets/1/) | Cycle aging. Cell: LithiumWerks APR18650M1B; Format: Cylindrical; Batteries: 64 | Cycle aging | ✅ Reference Performance Test(RPT) is performed | [Rapid estimation of lithium-ion battery capacity and resistances from short duration current pulses](https://doi.org/10.1016/j.jpowsour.2024.235813) | |
| [Li et al, 2025 (LFP-Gr)](https://digitalcommons.lib.uconn.edu/reil_datasets/3/) | Cycle aging, second-life. Cell: LithiumWerks APR18650M1B; Format: Cylindrical; Batteries: 106 | Cycle aging, second-life | ✅ RPT labels| [Forecasting battery capacity for second-life applications using physics-informed recurrent neural networks](https://www.sciencedirect.com/science/article/pii/S2590116825000396) | |
| [Schaeffer et al, 2024 (LFP-Gr)](https://zenodo.org/records/13715694) | Electrochemical battery dataset. Format: System; Batteries: 28 | Electrochemical Data Analysis | ❌ | [Gaussian process-based online health monitoring and fault analysis of lithium-ion battery systems from field data](https://www.sciencedirect.com/science/article/pii/S2666386424005630) | |

### NCA (LiNiₓCoᵧAl₁₋ₓ₋ᵧO₂ 镍钴铝酸锂) [三元锂电池]

| Dataset | Description | Task | Data Labeled or Not | Paper | Code |
| --- | --- | --- | --- | --- | --- |
| [Stroebl et al, 2024 (NCA-GrSi)](https://figshare.com/articles/dataset/Multi-Stage_Lithium_Ion_Battery_Aging_Study/25975315) | Comprehensive calendar+cycle aging. Cell: Samsung INR21700-50E; Format: Cylindrical; Batteries: 279; Measurements: Charge-discharge, Pulses | Comprehensive calendar+cycle aging | ✅ discharge capacity and internal resistance | [A multi-stage lithium-ion battery aging dataset using various experimental design methodologies](https://www.nature.com/articles/s41597-024-03859-z) |  |
| [Frie et al, 2024 (NCA-GrSi)](https://publications.rwth-aachen.de/record/973674) | Calendar aging. Cell: Samsung INR18650-35E; Format: Cylindrical; Batteries: 54; Measurements: Charge-discharge, Pulses | Calendar aging |❌| [An Analysis of Calendaric Aging over 5 Years of Ni‐Rich 18650‐Cells with Si/C Anodes](https://chemistry-europe.onlinelibrary.wiley.com/doi/10.1002/celc.202400020) | |
| [Wildfeuer et al, 2023 (NCA-GrSi)](https://mediatum.ub.tum.de/1713382) | Combined calendar & dynamic cyclic aging dataset with constant, alternating and time-varying stress conditions. Cell: Sony/Murata US18650-VTC5; Format: Cylindrical; Batteries: 196; Measurements: Charge-discharge, Pulses | Comprehensive calendar + cycle aging | ✅ discharge capacity and DIC internal resistance | [Experimental degradation study of a commercial lithium-ion battery](https://www.sciencedirect.com/science/article/pii/S0378775322014756) | |
| [Geslin et al, 2025 (NCA-GrSi)](https://purl.stanford.edu/td676xr4322) | Cycle aging. Format: Cylindrical; Batteries: 92; Measurements: Charge-discharge, Pulses, Application cycle | Cycle aging | ✅ raw data and aging summary file for each cell | [Dynamic cycling enhances battery lifetime](https://doi.org/10.1038/s41560-024-01675-8) | Stanford Digital Repository |
| [van Vlijmen et al, 2023 (NCA-Gr)](https://data.matr.io/10/) | Cycle aging. Cell: Tesla Model 3; Format: Cylindrical; Batteries: 236; Measurements: Charge-discharge, Pulses | Cycle aging + SOH estimation| ✅ RPT labels | [Diagnostic-free onboard battery health assessment](https://www.sciencedirect.com/science/article/pii/S2542435125001916) | Toyota Research Institute |
| [Kim et al, 2025 (NCA-GrSi)](https://data.mendeley.com/datasets/zn82y35zr8/4) | Cycle aging. Cell: Samsung INR 18650-30Q; Format: Cylindrical; Batteries: 60 | Cycle aging |✅ SOH, capacity, DCIR, knee cycle number labels| [Detection of the knee point in lithium-ion battery degradation using a state-of-charge-dependent parameter](https://www.pnas.org/doi/10.1073/pnas.2424838122) | |
| [Jöst et al, 2021 (NCA-GrSi)](https://publications.rwth-aachen.de/record/815749/files/TimeSeriesData.zip)| Cycle aging. Format: Cylindrical; Batteries: 28 | Cycle aging |✅ standardized check up tests were performed| [Timeseries data of a drive cycle aging test of 28 high energy NCA/C+Si round cells of type 18650](https://publications.rwth-aachen.de/record/815749) | |
| [Juarez-Robles, 2020 (NCA-Gr)](https://batteryarchive.org/cycle_list.html?t=0001) | Cycle aging. Cell: NCR18650B; Format: Cylindrical; Batteries: 21 | Cycle aging | ✅ SOH label | [Degradation-Safety Analytics in Lithium-Ion Cells: Part I. Aging under Charge/Discharge Cycling](https://iopscience.iop.org/article/10.1149/1945-7111/abc8c0/meta) | |

### LCO (LiCoO₂ 钴锂氧化物)

| Dataset | Description | Task | Data Labeled or not | Paper | Code |
| --- | --- | --- | --- | --- | --- |
| [NASA Randomized Battery Usage(LCO)](https://phm-datasets.s3.amazonaws.com/NASA/5.+Battery+Data+Set.zip) | NASA Battery Data Set. A dataset of lithium-ion battery experiments, including charging and discharging at different temperatures | RUL Prediction, Degradation Modeling |✅ SOH, RUL and impedance degradation labels | [A framework for Li-ion battery prognosis based on hybrid Bayesian physics-informed neural networks](https://www.nature.com/articles/s41598-023-33018-0#data-availability) | [[Github 12]](https://github.com/nasa/Li-ion-Battery-Prognosis-Based-on-Hybrid-Bayesian-PINN) |
| [Zhang et al, 2020 (LCO-Gr)](http://doi.org/10.5281/zenodo.3633835) | Cycle aging, EIS. Cell: Eunicell LR2032; Format: Coin; Batteries: 12 | Cycle aging, EIS | ❌ raw capacity and EIS data | [Identifying degradation patterns of lithium ion batteries from impedance spectroscopy using machine learning](https://www.nature.com/articles/s41467-020-15235-7) | |
| [Diao et al, 2019 (LCO-Gr)](https://calce.umd.edu/battery-accelerated-cycle-life-testing-data) | Electrochemical battery dataset. Format: Pouch; Batteries: 192 | Electrochemical Data Analysis | ✅ SOH labels | [Accelerated cycle life testing and capacity degradation modeling of LiCoO₂-graphite cells](https://www.sciencedirect.com/science/article/abs/pii/S0378775319308237) | |
| [He et al, 2011 (LCO-Gr)](https://calce.umd.edu/battery-data#CS2) | Cycle aging. Cell: CS2; Format: Prismatic; Batteries: 15 | Cycle aging |❌| [Prognostics of lithium-ion batteries based on Dempster–Shafer theory and the Bayesian Monte Carlo method](https://www.sciencedirect.com/science/article/abs/pii/S0378775311015400) | |
| [He et al, 2011 (LCO-Gr)](https://calce.umd.edu/battery-data#CX2) | Cycle aging. Cell: CX2; Format: Prismatic; Batteries: 12 | Cycle aging |❌ | [Prognostics of lithium-ion batteries based on Dempster–Shafer theory and the Bayesian Monte Carlo method](https://www.sciencedirect.com/science/article/abs/pii/S0378775311015400) | |
| [Saxena et al, 2016 (LCO-Gr)](https://calce.umd.edu/battery-data#PL) | Cycle aging. Cell: PL; Format: Pouch; Batteries: 16 | Cycle aging | ✅ The experiment runs standardized full CCCV/CC characterization tests every 50 or 100 partial cycles | [Cycle life testing and modeling of graphite/LiCoO₂ cells under different state of charge ranges](https://www.sciencedirect.com/science/article/abs/pii/S0378775316309247) | |
| [Navidi et al, 2026 (LCO-Gr)](https://digitalcommons.lib.uconn.edu/reil_datasets/4/) | Cycle aging, BOL. Cell: Powerstream LiR 2032; Format: Coin; Batteries: 76 | Cycle aging, BOL | ✅ Benchmark cycling RPT labels| [UConn LCO/Gr battery fast charging dataset](https://pubs.rsc.org/en/content/articlelanding/2026/ta/d5ta09520d) | |

### NMC (LiNiₓMnᵧCo₁₋ₓ₋ᵧO₂ 镍钴锰酸锂)  [三元锂电池]

| Dataset | Description | Task | Data Labeled or Not | Paper | Code |
| --- | --- | --- | --- | --- | --- |
| [RADAR4KIT(NMC/C-SiO)](https://radar.kit.edu/radar/en/search?query=Comprehensive+battery+aging+dataset%3A+capacity+and+impedance+fade+measurements+of+a+lithium-ion+NMC%2FC-SiO+cell&_csrf=4f078a89-8f12-487b-9500-6b0b510eac1d) | It contains over 3 billion data points from 228 commercial NMC/C+SiO lithium-ion cells aged for more than a year under a wide range of operating conditions | Aging Analysis, Calendar and Cyclic Aging |❌| [Comprehensive battery aging dataset: capacity and impedance fade measurements of a lithium-ion NMC/C-SiO cell](https://www.nature.com/articles/s41597-024-03831-x#Sec8) | [[Github 5]](https://github.com/energystatusdata/bat-age-data-scripts) |
| [Cui et al, 2024 (SC_NMC-Gr)](https://data.matr.io/8/) | Formation, Cycle aging. Cell: LiFun; Format: Pouch; Batteries: 186 | Formation, Cycle aging |✅ RUL and SOH labels| [Systematic feature design for cycle life prediction of lithium-ion batteries during formation](https://www.sciencedirect.com/science/article/pii/S2542435124003532) | |
| [Weng et al, 2021 (NMC111-Gr)](https://deepblue.lib.umich.edu/data/concern/data_sets/b2773w109) | Formation, Cycle aging. Cell: Custom; Format: Pouch; Batteries: 40 | Formation, Cycle aging |❌| [Predicting the impact of formation protocols on battery lifetime immediately after manufacturing](https://doi.org/10.1016/j.joule.2021.09.015) | |
| [SL_Dataset_SECL_INR21700-M50T.zip(NMC)](https://osf.io/8jnr5/overview) | contains second-life experimental data collected at Stanford Energy Control Lab for six NMC cells cycled using residential and commercial synthetic duty cycles. | Second-life Battery Aging Study |✅ RPT capacity/impedance labels| [Second-life lithium-ion battery aging dataset based on grid storage cycling](https://www.sciencedirect.com/science/article/pii/S2352340924010084/pdfft?md5=c609784fde9bd4614d991071b09b780d&pid=1-s2.0-S2352340924010084-main.pdf) | |
| [Dataset_SECL_INR21700-M50T(NMC)](https://www.dropbox.com/sh/oqns43ajz2xn7ga/AAAs5MINIiUnOv6Elch822y-a?dl=0) | The INR21700-M50T battery cells with graphite/silicon anode and Nickel-Manganese-Cobalt cathode were tested over a period of 28 months | Aging Analysis | ✅ SOH and RUL labels| [Lithium-ion battery aging dataset based on electric vehicle real-driving profiles](https://www.sciencedirect.com/science/article/pii/S2352340922002062?via%3Dihub) | |
| [Cycle aging data of automotive-grade lithium ion battery cells under realistic and accelerated load conditions(NMC)](https://mediatum.ub.tum.de/1748915) | This data set contains cycle aging data from three automotive-grade NMC Gr pouch cells (used in the VW ID.3) subjected to three different usage patterns over a duration of 3+ years | Realistic and Accelerated Aging Test Analysis |❌| [Cycle aging data of automotive-grade lithium ion battery cells under realistic and accelerated load conditions](https://www.sciencedirect.com/science/article/pii/S2352152X25000702#d1e2292) | [[Github 15]](https://mediatum.ub.tum.de/1748915) |
| [Schmitt et al, 2024 (NMC811-GrSi)](https://mediatum.ub.tum.de/1690455) | Cycle aging. Cell: LG INR18650-MJ1; Format: Cylindrical; Batteries: 10; Measurements: Charge-discharge, Pulses, Application cycle, Charge rate sweep | Cycle aging |✅ SOH labels | [Change in the half-cell open-circuit potential curves of silicon–graphite and nickel-rich lithium nickel manganese cobalt oxide during cycle aging](https://www.sciencedirect.com/science/article/pii/S2352152X22025063) | |
| [Kim et al, 2024 (NMC811-GrSi)](https://data.mendeley.com/datasets/h2y7mj4kt7/2) | Cycle aging. Cell: LG INR18650-MJ1; Format: Cylindrical; Batteries: 72 | Cycle aging | ❌| [Degradation path prediction of lithium-ion batteries under dynamic operating sequences](https://pubs.rsc.org/en/content/articlehtml/2025/ee/d4ee04787g) | |
| [Fly et al, 2025 (NMC811-Gr)](https://repository.lboro.ac.uk/articles/dataset/Underlying_data_Influence_of_periodic_temperature_variations_on_calendar_ageing_of_lithium-ion_batteries_/26870248?file=57211955) | Calendar aging. Cell: LG INR-21700 M50LT; Format: Cylindrical; Batteries: 28 | Calendar aging |✅ RPT labels| [Influence of periodic temperature variations on calendar ageing of lithium-ion batteries](https://www.sciencedirect.com/science/article/pii/S0378775325019834) | |
| [Bills et al, 2023 (NMC-Gr)](https://kilthub.cmu.edu/articles/dataset/eVTOL_Battery_Dataset/14226830/2) | Cycle aging. Cell: Sony-Murata 18650 VTC-6; Format: Cylindrical; Batteries: 22 | Cycle aging | ✅ with capacity tests every 50 cycles | [A battery dataset for electric vertical takeoff and landing aircraft](https://www.nature.com/articles/s41597-023-02180-5) | |
| [Yao et al, 2024 (NMC-Gr)](https://data.mendeley.com/datasets/m8w8sjk3vm/2) | Cycle aging. Cell: EEMB Battery LIR2025H; Format: Coin; Batteries: 45 | Cycle aging | ❌ | [A physics–guided machine learning approach for capacity fading mechanism detection and fading rate prediction using early cycle data](https://www.mdpi.com/2313-0105/10/8/283) | |
| [Nowacki et al, 2025 (NMC-Gr)](https://digitalcommons.lib.uconn.edu/reil_datasets/2/) | Cycle aging. Cell: Panasonic UR18650AA; Format: Cylindrical; Batteries: 44 | Cycle aging |✅ RPT labels| [Fine-tuning for rapid capacity estimation of lithium-ion batteries](https://doi.org/10.1016/j.ensm.2025.104425) | |
| [Gasper et al, 2022 (NMC-Gr)](https://github.com/NREL/battery_capacity_from_eis) | Cycle aging. Batteries: 32 | Cycle aging | ✅ used machine learning to develop models predicting battery capacity | [Predicting battery capacity from impedance at varying temperature and state of charge using machine learning](https://www.sciencedirect.com/science/article/pii/S2666386422005021) | [[Github]](https://github.com/NREL/battery_capacity_from_eis) |
| [Li et al, 2021 (NMC-Gr)](https://publications.rwth-aachen.de/record/818642) | Cycle aging of "grade C" commercial cells. Cell: Sanyo/Panasonic UR18650E; Format: Cylindrical; Batteries: 48; Measurements: Charge-discharge, RPT | Cycle aging of "grade C" commercial cells |✅ RPT labels| [One-shot battery degradation trajectory prediction with deep learning](https://doi.org/10.1016/j.jpowsour.2021.230024) | |
| [Mowri et al, 2024 (NMC811-GrSi)](https://data.mendeley.com/preview/rvhjw633df) | Constant-current first life, drive cycle second life. Cell: LG INR21700-M50; Format: Cylindrical; Batteries: 18; Measurements: Charge-discharge, RPT, SEM, EDX | Constant-current first life, drive cycle second life | #dataset not found | [Assessing the Impact of First-Life Lithium-Ion Battery Degradation on Second-Life Performance](https://ideas.repec.org/a/gam/jeners/v17y2024i2p501-d1322750.html) | |
| [Wang et al, 2024 (NMC-Gr)](https://zenodo.org/records/10963339) | Cycle aging. Cell: Lishen 18650; Format: Cylindrical; Batteries: 55 | Cycle aging | ✅ SOH labels | [Physics-informed neural network for lithium-ion battery degradation stable modeling and prognosis](https://www.nature.com/articles/s41467-024-48779-z) | |
| [Kirkaldy et al, 2022 (NMC-GrSi)](https://zenodo.org/records/7235858) | Cycle aging. Cell: LG 18650 M50T; Format: Cylindrical; Batteries: 17 | Cycle aging | ✅ RPT labels| [Lithium-Ion Battery Degradation: Measuring Rapid Loss of Active Silicon in Silicon–Graphite Composite Electrodes](https://pubs.acs.org/doi/10.1021/acsaem.2c02047) | |
| [Goldammer et al, 2022 (NMC-Gr)](https://ieee-dataport.org/open-access/sicwell-dataset) | Cycle aging. Format: Pouch; Batteries: 42 | Cycle aging | ✅ SOH labels| [The impact of an overlaid ripple current on battery aging: The development of the SiCWell dataset](https://www.mdpi.com/2313-0105/8/2/11) | |
| [Smith et al, 2017 (NMC-Gr)](https://batterydata.energy.gov/data-repo/dataset/71c72c7b-39e3-4748-90f0-2d631c0f1df8) | Cycle aging. Cell: Kokam; Format: Pouch; Batteries: 11 | Cycle aging |❌| [Life prediction model for grid-connected Li-ion battery energy storage system](https://ieeexplore.ieee.org/abstract/document/7963578/) | |
| [Tanim et al, 2021 (NMC532-Gr)](https://batterydata.energy.gov/data-repo/dataset/7c32de89-7d95-4812-9e04-f3770c91babe/detail) | Cycle aging, fast charging. Cell: Custom; Format: Pouch; Batteries: 34 | Cycle aging, fast charging |❌| [Extended cycle life implications of fast charging for lithium-ion battery cathode](https://doi.org/10.1016/j.ensm.2021.07.001) | |
| [Popp et al, 2024 (NMC811-Gr)](https://zenodo.org/records/10891871) | state estimation. Cell: Samsung INR21700-50E; Format: Cylindrical; Batteries: 143 | SOH and RUL prediction |✅ CCCV full charge + 0.5C full discharge test is performed to measure the true usable capacity of each cell | [Fast Screening and Sorting of Commercially Available Second-Life Batteries from Former Mobility Applications for Construction of Small Energy Storage Systems](https://ieeexplore.ieee.org/abstract/document/10599066) | |
| [Lithium Inventory Tracking as a Nondestructive Battery Evaluation and Monitoring Method](https://osf.io/2w4k3) | There are twelve datasets in .csv format, containing charge and discharge cycles of twelve Li–LixNi0.8Mn0.1Co0.1O2 (NMC 811) cells made of various cell formulations and configurations and subjected to tests under different protocols and conditions. | Nondestructive Battery Evaluation, Lithium Inventory Tracking |❌| [Lithium Inventory Tracking as a Nondestructive Battery Evaluation and Monitoring Method](https://doi.org/10.17605/OSF.IO/2W4K3) | |
| [UofM Pouch Cell Voltage and Expansion Cyclic Aging Dataset](https://deepblue.lib.umich.edu/data/concern/data_sets/5d86p0488)|for studying the capability of aging diagonistic using cell expansion under variety of aging states and condition. Custom pouch cells were cycled under various conditions while simultaneously measuring voltage, current, temperature, and cell expansion (thickness changes), with periodic HPPC, EIS, and C-rate tests to link mechanical behavior to electrical aging and degradation modes|cycle aging analysis & degradation diagnosis based on cell swelling /mechanical expansion |✅ C/20 full charge-discharge test label| [UofM Pouch Cell Voltage and Expansion Cyclic Aging Dataset](https://doi.org/10.7302/7tw1-kc35)|

### LMO (LiMn₂O₄ 锰酸锂)

| Dataset | Description | Task | Data Labeled or Not | Paper | Code |
| --- | --- | --- | --- | --- | --- |
| [Beatty et al, 2025 (LMO/LNO-Gr)](https://repository.lboro.ac.uk/articles/online_resource/Long-Term_Sweat_Testing_Data_for_Second-Life_Batteries/28732490/2) | Cycle aging. Cell: Nissan Leaf; Format: Pouch; Batteries: 6 | Cycle aging |✅The long-term cycling (sweat test) experiments were interspersed with periodic full capacity calibration tests (equivalent to RPT) | [Long-Term Sweat Testing Dataset for Second-Life Batteries](https://www.nature.com/articles/s41597-025-05360-7) | |

### 复合数据 (混合化学体系)

| Dataset | Description | Task | Data Labeled or Not | Paper | Code |
| --- | --- | --- | --- | --- | --- |
| [batteryarchive.org(LCO NMC-LCO LFP NCA NMC)](https://www.batteryarchive.org/cycle_list.html?time=0001) | A repository for easy visualization, analysis, and comparison of battery data across institutions. | Data Visualization, Analysis, and Comparison |✅ SOH, capacity fade, RUL labels| [Degradation of Commercial Lithium-Ion Cells as a Function of Chemistry and Cycling Conditions](https://iopscience.iop.org/article/10.1149/1945-7111/abae37) | |
| [University of Maryland CALCE(LCO LFP NMC)](https://calce.umd.edu/battery-data) | Battery form factors include cylindrical, pouch, and prismatic, and the chemistries include LCO, LFP, and NMC | State Estimation, RUL Prediction, Degradation Modeling |✅ SOC and SOH labels | [Evaluation of the Safety Standards System of Power Batteries for Electric Vehicles in China](https://www.sciencedirect.com/science/article/abs/pii/S0306261923010383?via%3Dihub) | |
| [Stanford Energy Control Lab(NMC NCA LFP)](https://onorilab.stanford.edu/products/code-and-data-set#:~:text=%2A%20Experimental%20data%20of%20lithium,driving%20profiles) | Stanford Energy Control Lab Code and Data Set | General Battery Research |✅ driving cycle logs + periodic RPT diagnostic files | | |
| [NASA Batteries(LCO NMC-LCO LNMC LFP LNCA)](https://phm-datasets.s3.amazonaws.com/NASA/5.+Battery+Data+Set.zip) | Experiments on Li-Ion batteries. Charging and discharging at different temperatures. Records the impedance as the damage criterion. The data set was provided by the NASA Prognostics Center of Excellence (PCoE). | Prognostics and Health Management (PHM) |✅ discharge capacity and  battery impedance | | |
| [CALCE Battery Data Archive(LCO LFP)](https://web.calce.umd.edu/batteries/data/) | The CALCE lithium battery dataset released by the University of Maryland is a valuable resource designed specifically for battery state-of-charge (SOC) prediction, state-of-health (SOH) assessment, and prognostics and health management (PHM) of batteries. | SOC Prediction, SOH Assessment, PHM |✅ SOH/RUL labels| [Prognostics of lithium-ion batteries based on Dempster–Shafer theory and the Bayesian Monte Carlo method](https://www.sciencedirect.com/science/article/abs/pii/S0378775311015400) | [[Github 18]](https://github.com/isea-rwth-aachen/battery-degradation-trajectory-prediction) |
| [Lam et al, 2025 (Mixed)](https://osf.io/ju325) | Calendar aging. Format: Mixed; Batteries: 232 | Calendar aging | ✅ summary files store capacity and resistance values as supervised learning labels for calendar battery degradation modeling| [A decade of insights: Delving into calendar aging trends and implications](https://www.sciencedirect.com/science/article/pii/S2542435124005105) ||
| [Heydarzadeh et al, 2025 (Mixed)](https://etsin.fairdata.fi/dataset/f60a7388-99b6-4637-96d5-8610a7f71612) | Cycle aging. Format: Cylindrical; Batteries: 8 | Cycle aging |❌| [Dataset of lithium-ion cell degradation under randomized current profiles for NMC, NCA, and LFP chemistries](https://www.sciencedirect.com/science/article/pii/S235234092500263X) | |
| [Lu et al, 2022 (LCO/NMC-Gr)](https://data.mendeley.com/datasets/kw34hhw7xg/3) | Cycle aging. Cell: LISHEN 18650; Format: Cylindrical; Batteries: 77 | Cycle aging |✅ SOH labels | [Battery degradation prediction against uncertain future conditions with recurrent neural network enabled deep learning](https://www.sciencedirect.com/science/article/pii/S2405829722002446) | |
| [Che et al, 2023 (Mixed)](https://data.mendeley.com/datasets/n3b54nsw8m/5) | Cycle aging. Format: Mixed; Batteries: 55.| Cycle aging |✅ SOH labels | [Data-driven battery degradation prediction under diverse usage conditions](https://www.sciencedirect.com/science/article/pii/S266638642300588X) | |
| [Jones et al, 2022 (LIB)](https://doi.org/10.5281/zenodo.6645536) | Cycle aging. Format: Coin; Batteries: 88 | Cycle aging |❌| [Impedance-based forecasting of lithium-ion battery performance amid uneven usage](https://www.nature.com/articles/s41467-022-32422-w) | |
| [Zhu et al, 2022 (Mixed)](https://zenodo.org/records/6405084) | cycle aging. Format: Cylindrical; Batteries: 3 | cycle aging |❌| [Data-driven capacity estimation of commercial lithium-ion batteries from voltage relaxation](https://www.nature.com/articles/s41467-022-29837-w) | |
| [Svaluto-Ferro et al, 2025 (Mixed)](https://zenodo.org/records/15481956) | Cycle aging. Cell: Custom; Format: Coin; Batteries: 199 | Cycle aging |❌| [Toward an autonomous robotic battery materials research platform powered by automated workflow and ontologized findable, accessible, interoperable, and reusable data management](https://chemistry-europe.onlinelibrary.wiley.com/doi/10.1002/batt.202500155) | |
| [Ward et al, 2024 (Mixed)](https://doi.org/10.18126/s90e-dq90) | Cycle aging. Cell: Custom; Format: Pouch; Batteries: 300 | Cycle aging |❌| [Multivariate prognosis of battery advanced state of health via transformers](https://doi.org/10.1016/j.xcrp.2024.101928) | |
| [Birkl & Howey, 2017 (n/a)](https://ora.ox.ac.uk/objects/uuid:03ba4b01-cfed-46d3-9b1a-7d4a7bdf6fac) | Cycle aging. Cell: Kokam SLPB533459H4; Format: Pouch; Batteries: 8 | Cycle aging |✅ SOH labels| | |
| [Bosello et al, 2021 (n/a)](https://data.mendeley.com/datasets/n6xg5fzsbv/1) | cycle aging. Batteries: 27 | cycle aging |✅ RPT| [Li-Ion Batteries State-of-Charge Estimation Using Deep LSTM at Various Battery Specifications and Discharge Cycles](https://dl.acm.org/doi/10.1145/3462203.3475878) | |
| [Pecht 2015 (n/a)](https://calce.umd.edu/battery-data#Storage) | Calendar aging. Batteries: 144; Measurements: Charge-discharge, EIS | Calendar aging |✅ RPT + EIS impedance tests taken| | |
| [XJTU Battery Health Monitoring and Prognostic Dataset](https://github.com/wang-fujin/Battery-dataset-preprocessing-code-library.git) | The repository contains Python scripts for handling specific well-known battery datasets, focusing on health monitoring and remaining useful life prediction. | Health Monitoring, RUL Prediction (Preprocessing Library) |✅ | [Battery-dataset-preprocessing-code-library](https://github.com/wang-fujin/Battery-dataset-preprocessing-code-library.git) | [[Github]](https://github.com/wang-fujin/Battery-dataset-preprocessing-code-library.git) |
| [Underlying dataset for battery pack degradation - Understanding aging in parallel-connected lithium-ion batteries under thermal gradients](https://zenodo.org/records/10207731) | raw and processed data and analysis codes to investigate aging in parallel-connected lithium-ion battery packs under thermal gradients| Battery Pack Aging, Thermal Gradient Effects |❌ | [Underlying dataset for battery pack degradation - Understanding aging in parallel-connected lithium-ion batteries under thermal gradients](https://doi.org/10.5281/zenodo.10207731) | |
|[Increasing generalization capability of battery health estimation using continual learning approach](https://data.mendeley.com/public-api/zip/n3b54nsw8m/download/9)| These datasets contain mixed lithium-ion pouch & prismatic cells aged under diverse temperatures and loading profiles, with partial charge-discharge Q curves and full cycle capacity records collected via Neware testers for continual learning SOH estimation research | SOH estimation |✅ charge and discharge capacity| [Battery aging datasets for "Increasing generalization capability of battery health estimation using continual learning approach"](https://data.mendeley.com/datasets/n3b54nsw8m/9)|


## 2. Battery Performance

### LFP (LiFePO₄ 磷酸铁锂)

| Dataset | Description | Task | Data Labeled or not | Paper | Code |
| --- | --- | --- | --- | --- | --- |
| [Fasolato et al, 2025 (LFP-Gr)](https://data.mendeley.com/datasets/ycx459r5c3/2) | BOL. Cell: CALB L148N58A; Format: Prismatic; Batteries: 11 | BOL | ✅ State of Charge, SOC | [A dataset for large prismatic lithium-ion battery cells (CALB L148N58A): Comprehensive characterization and real-world driving cycles](https://www.sciencedirect.com/science/article/pii/S2352340925000332) | |
| [Gao and Onori, 2026 (LFP-Gr)](https://github.com/yizhaogao2025/LFP_battery_SOC_Dataset) | SOC estimation. Format: Cylindrical; Batteries: 1 | SOC estimation | ✅ State of Charge, SOC | [Advancing LiFePO₄ battery SOC estimation: Electrochemical impedance spectroscopy with short-period sine-wave pulses](https://www.sciencedirect.com/science/article/pii/S2773153725001367) | [[Github]](https://github.com/yizhaogao2025/LFP_battery_SOC_Dataset) |
| [Xing et al, 2014 (LFP-Gr)](https://calce.umd.edu/battery-data#A123) | BOL. Cell: A123 18650; Format: Cylindrical; Batteries: 1 | BOL | ✅ State of Charge, SOC; State of Health, SOH; Remaining Useful Life, RUL | [State of charge estimation of lithium-ion batteries using the open-circuit voltage at various ambient temperatures](https://www.sciencedirect.com/science/article/pii/S0306261913005746) | |
| [Kumtepeli et al, 2026 (LFP-Gr)](https://doi.org/10.5287/ora-eonzaxjpm) | Echem, thermal, modeling dode. Cell: A123; Format: Pouch; Batteries: 1 | Echem, thermal, modeling dode | ✅ Relative State of Charge (RSOC)； Absolute State of Charge (ASOC)； Remaining Capacity (Ah)； Full Charge Capacity (FCC)； aim for Electrochemical-thermal modeling| [Electrochemical–thermal modelling of high power Li-ion pouch cells](https://www.sciencedirect.com/science/article/pii/S037877532502600X) | |

### NCA (LiNiₓCoᵧAl₁₋ₓ₋ᵧO₂ 镍钴铝酸锂)  [三元锂电池]

| Dataset | Description | Task | Data Labeled or not | Paper | Code |
| --- | --- | --- | --- | --- | --- |
| [Panasonic 18650PF Li-ion Battery Data(NCA)](https://data.mendeley.com/datasets/wykht8y7tg/1) | The included tests were performed at the University of Wisconsin-Madison by Dr. Phillip Kollmeyer. If this data is utilized for any purpose, it should be appropriately referenced. The tests can be used to test Neural Network and Kalman Filter State of Charge algorithms, or to develop battery models, and are intended to be a reference so researchers can compare their algorithm and model performance for a standard data set. | SOC Estimation, Battery Modeling | ✅ State of Charge, SOC| [Intrinsic Variability in the Degradation of a Batch of Commercial 18650 Lithium-Ion Cells](https://www.mdpi.com/1996-1073/11/5/1031) | [[Github 20]](https://github.com/infinityengi/li-ion-battery-datasets) |

### NMC (LiNiₓMnᵧCo₁₋ₓ₋ᵧO₂ 镍钴锰酸锂)  [三元锂电池]

| Dataset | Description | Task | Data Labeled or not | Paper | Code |
| --- | --- | --- | --- | --- | --- |
| [WMG Calendar Ageing Dataset - LGM50 Commercial Cells (39 Storage Conditions)](https://zenodo.org/records/14577286) | The dataset presents comprehensive calendar aging data collected from commercial LGM50 lithium-ion cells under controlled storage conditions: Storage Temperatures: 0°C, 25°C, and 45°C; State of Charge (SOC): 13 distinct levels per temperature condition; Test Duration: Two-years per condition (on average). The dataset consists of MATLAB (.mat) files containing cell cycling results from Reference Performance Tests (RPTs) conducted throughout the aging study. | Calendar Aging, RPT | ✅ Capacity Fade；Resistance Increase | [WMG Calendar Ageing Dataset - LGM50 Commercial Cells](https://doi.org/10.5281/zenodo.14577286) | |
| [Data from: "Lithium-ion battery degradation: comprehensive cycle ageing data and analysis for commercial 21700 cells"](https://zenodo.org/records/10637534) | These data were generated from battery cell ageing experiments that included break-in cycles and Reference Performance Tests (RPTs), alternating with performance checks and ageing cycles. Each cell was base-cooled at set temperatures using bespoke rigs, with full experimental details available in linked publications. The repository is structured according to each "Experiment," containing folders for "Summary Data," "Processed Timeseries Data," and "Raw Data." | Comprehensive Cycle Ageing, RPT | ✅ Capacity Fade(C/10 Capacity, C/2 Capacity); Resistance Increase (0.1s Resistance); Degradation Mode Analysis, DMA ( LLI（锂离子损失）、LAM-PE（正极活性物质损失）、LAM-NE（负极活性物质损失）、LAM-NE-Gr（负极石墨活性物质损失）和 LAM-NE-Si（负极硅活性物质损失）)| [Data from: "Lithium-ion battery degradation...](https://doi.org/10.5281/zenodo.10637534) | |
| [Faraji-Niri et al, 2023 (NMC811-GrSi)](https://data.mendeley.com/datasets/mn9fb7xdx6/3) | EIS. Cell: LG INR21700-M50; Format: Cylindrical; Batteries: 30; Measurements: Charge-discharge, Pulses, EIS | EIS | ✅ State of Charge, SOC | [Accelerated state of health estimation of second life lithium-ion batteries via electrochemical impedance spectroscopy tests and machine learning techniques](https://www.sciencedirect.com/science/article/pii/S2352152X22022848) | |
| [Kollmeyer & Skells, 2020 (NMC-Gr)](https://data.mendeley.com/datasets/9xyvy2njj3/1) | BOL. Cell: Samsung INR21700 30T; Format: Cylindrical; Batteries: 1 | BOL | ✅ State of Charge, SOC | | |
| [Khan et al, 2025 (NMC-GrSi)](https://osf.io/9ceav) | BOL. Cell: Molicell INR-21700-P42A; Format: Cylindrical; Batteries: 12 | BOL | ✅ State of Charge, SOC; aim for 电池的端电压（Terminal Voltage） | [High-power lithium-ion battery characterization dataset for stochastic battery modeling](https://www.nature.com/articles/s41597-025-05725-y) | |
| [Uppaluri et al, 2025 (NMC811-Li)](https://osf.io/5dqwg/?view_only=608e4c22acdd483591d1d55b74a81401) | commerical Li-metal. Cell: Sakuu; Batteries: 23 | commerical Li-metal | ✅ voltage; State of Charge, soc; State of Health, soh; chemistry; second_life_class| [Lithium-metal battery degradation dataset from continuous cycling experiments](https://www.sciencedirect.com/science/article/pii/S2352340925005141) | |
| [Khan et al, 2025 (NMC-Gr)](https://www.sciencedirect.com/science/article/pii/S2352340925010030) | Cycle aging, EIS vs SOC. Format: Prismatic; Batteries: 22 | Cycle aging, EIS vs SOC | ✅ State of Health, SOH| [Electrochemical impedance spectroscopy of prismatic lithium-ion batteries across state of charge and aging conditions](https://www.sciencedirect.com/science/article/pii/S2405896325001132) | |
| [Jackowska et al, 2025 (SC_NMC)](https://github.com/Battery-Intelligence-Lab/Jackowska-2025-JPS) | BOL + model parameterization. Format: Coin; Batteries: 1 | BOL + model parameterization | ❌ | [Transport limitations in single-crystal NCM cathode electrodes](https://www.sciencedirect.com/science/article/pii/S037877532502717X) | [[Github]](https://github.com/Battery-Intelligence-Lab/Jackowska-2025-JPS) |
| [Xing et al, 2014 (NMC-Gr)](https://calce.umd.edu/battery-data#INR) | BOL. Cell: 18650-20R; Format: Cylindrical; Batteries: 1 | BOL | ✅ State of Charge, SOC; State of Health, SOH; Remaining Useful Life, RUL| [State of charge estimation of lithium-ion batteries using the open-circuit voltage at various ambient temperatures](https://www.sciencedirect.com/science/article/pii/S0306261913005746) | |
| [Huang and Zeier, 2026 (NMC-LPSC-Li (SSE))](https://data-management.uni-muenster.de/datastore/download/10.17879/40978460882) | BOL. Cell: Custom; Format: Coin; Batteries: 1 | BOL | ✅： for Joint-domain impedance spectroscopy| [Joint-domain impedance spectroscopy for solid-state batteries: Enabling accelerated characterization and data-driven insights](https://pubs.acs.org/doi/full/10.1021/acsenergylett.5c03055) | |


### 复合数据 (混合化学体系)

| Dataset | Description | Task | Data Labeled or not | Paper | Code |
| --- | --- | --- | --- | --- | --- |
| [Full factorial design of experiments dataset for parallel-connected lithium-ion cells imbalanced performance investigation(NCA NMC)](https://data.mendeley.com/datasets/zh58byr53c/1) | A total of 54 test conditions were investigated under various operating temperatures, cell-to-cell interconnection resistance, cell chemistry, and aging levels. | Imbalanced Performance Investigation | ✅ Discharge Capacity; Ohmic Resistance | [Unveiling the performance impact of module level features on parallel-connected lithium-ion cells via explainable machine learning techniques on a full factorial design of experiments](https://www.sciencedirect.com/science/article/pii/S2352152X24003670/pdfft?md5=6771186db4779d082b7ea8ac52ce3987&pid=1-s2.0-S2352152X24003670-main.pdf) | |
| [Data-driven capacity estimation of commercial lithium-ion batteries from voltage relaxation(NCA NCM NCM+NCA)](https://doi.org/10.5281/zenodo.6379165) | Experimental cycling data for three commercial 18650 type batteries (NCA, NCM, and NCM+NCA chemistries). The dataset provides cycling data, impedance measurements, and detailed descriptions of voltage relaxation tests. | Capacity Estimation | ✅ Cycle Life; Cycle Life Classification | [Data-driven capacity estimation of commercial lithium-ion batteries from voltage relaxation](https://www.nature.com/articles/s41560-019-0356-8) | [[Github 13]](https://github.com/Yixiu-Wang/data-driven-capacity-estimation-from-voltage-relaxation) |
| [Figgener et al, 2024 (Mixed)](https://doi.org/10.5281/zenodo.12091223) | Real world use. Format: System; Batteries: 21; Measurements: Charge-discharge, Real-world | Real world use | ✅ Usable Capacity Fade（Usable Capacity (Ah) ；State of Health (SOH, %)；Capacity Fade Rate (% per year)）| [Multi-year field measurements of home storage systems and their use in capacity estimation](https://www.nature.com/articles/s41560-024-01620-9) | |
| [Sørensen et al, 2023 (Li-ion)](https://zenodo.org/records/12730566) | Real world use. Format: EV; Batteries: 267; Measurements: Real-world | Real world use | ✅ Capacity Loss; State of Health (SOH) | [Real-world electric vehicle battery data for energy consumption and driving range analysis](https://www.sciencedirect.com/science/article/pii/S2352467723002035) | |
| [Lucas et al, 2024 (Mixed)](https://doi.org/10.18154/RWTH-2024-04895) | Real world use. Format: System; Batteries: 11; Measurements: Real-world | Real world use | ✅ Remaining Useful Life (RUL); SOH Single-point Estimation; SOH Degradation Trajectory | [Energy management of stationary hybrid battery energy storage systems using the example of a real-world 5 MW hybrid battery storage project in Germany](https://doi.org/10.1016/j.est.2022.104257) | |
| [Catenaro & Onori, 2021 (Mixed)](https://data.mendeley.com/datasets/kxsbr4x3j2/2) | BOL. Format: Cylindrical; Batteries: 18 | BOL |  ✅ Discharge Capacity (Ah)； State of Charge (SOC, %) | [Experimental data of lithium-ion batteries under galvanostatic discharge tests at different rates and temperatures of operation](https://www.sciencedirect.com/science/article/pii/S2352340921001785) | |
| [Piombo et al, 2024 (Mixed)](https://data.mendeley.com/datasets/zh58byr53c/2) | module currents. Cell: NCA Samsung INR21700-50E and NMC LG-Chem INR21700-M50T; Format: Cylindrical, System; Batteries: 40 | module currents | ✅ Discharge Capacity (Ah)；Ohmic Resistance (Ω) | [Unveiling the performance impact of module level features on parallel-connected lithium-ion cells via explainable machine learning techniques on a full factorial design of experiments](https://www.sciencedirect.com/science/article/pii/S2352152X24003670) | |
| [Shrivastava & Soon, 2022 (Mixed)](https://data.mendeley.com/datasets/29kw38kzwj/1) | BOL. Cell: Panasonic NCR18650B, A123 (LithiumWerks) APR18650M1B; Format: Cylindrical; Batteries: 2 | BOL | ✅ State of Charge (SOC); State of Energy (SOE); State of Power (SOP); Maximum Available Capacity (Ah)	; Maximum Available Energy (Wh)	| [Comprehensive co-estimation of lithium-ion battery state of charge, state of energy, state of power, maximum available capacity, and maximum available energy](https://doi.org/10.1016/j.est.2022.106049) | |
| [Kollmeyer, 2018 (LIB)](https://data.mendeley.com/datasets/wykht8y7tg/1) | BOL. Cell: Panasonic 18650PF; Format: Cylindrical; Batteries: 1 | BOL | ✅ State of Charge, SOC; Terminal Voltage | | |
| [Kollmeyer et al, 2020 (LIB)](https://data.mendeley.com/datasets/b5mj79w5w9/2) | BOL. Cell: LG 18650HG2; Format: Cylindrical; Batteries: 1 | BOL | ✅ State of Charge (SOC, %) | [Robust xEV battery state-of-charge estimator design using a feedforward deep neural network](https://www.sae.org/publications/technical-papers/content/2020-01-1181/) | |
| [Gasper et al, 2025 (Mixed)](https://zenodo.org/records/14597394) | state estimation. Format: Mixed; Batteries: 79 | state estimation | ✅ Discharge Capacity; US06 Drive Cycle Charge Throughput; FCR Cycle Charge Efficiency; Safety Metric| [Searching for a Pulse: Evaluating the Use of Rapid DC Pulses for Diagnosing Battery Health, State-of-Charge, and Safety](https://iopscience.iop.org/article/10.1149/1945-7111/addd50) | |
| [Fernando et al, 2024 (LFP-Gr, NMC811-GrSi)](https://doi.org/10.17632/y8nstxmdrg.1) | BOL. Cell: LG 18650 MJ1, LithiumWerks APR 18650 M1B; Format: Cylindrical; Batteries: 2 | BOL | ✅ Open-Circuit Voltage (OCV); Relaxed Voltage | [Cell-to-cell variability and thermal-electrical performance of commercial cylindrical lithium-ion batteries](https://www.cell.com/cell-reports-physical-science/fulltext/S2666-3864(23)00599-4) | |
| [Tao et al, 2024 (Mixed)](https://zenodo.org/records/13360631) | state estimation. Format: Mixed; Batteries: 270 | state estimation | ✅ State of Health (SOH) | [Generative learning assisted state-of-health estimation for sustainable battery recycling with random retirement conditions](https://www.nature.com/articles/s41467-024-54454-0) | |
| [He et al, 2023 (Mixed)](https://figshare.com/articles/dataset/EVBattery_A_Large-Scale_Electric_Vehicle_Dataset_for_Battery_Health_and_Capacity_Estimation/23301881) | EV pack data. Format: Pack; Batteries: 464 | EV pack data | ✅ Battery Health; Battery Capacity | [EVBattery: A large-scale electric vehicle dataset for battery health and capacity estimation](https://arxiv.org/pdf/2201.12358) | |
| [Liu et al, 2025 (Mixed)](http://ivstskl.changan.com.cn/?p=2697) | EV pack data. Format: Pack; Batteries: 300 | EV pack data | ✅ | [Multi-modal framework for battery state of health evaluation using open-source electric vehicle data](https://www.nature.com/articles/s41467-025-56485-7) | |
| [Marzook et al, 2025 (LIB)](https://zenodo.org/records/7385979) | BOL thermal and electrical performance. Format: Cylindrical; Batteries: 6 | BOL thermal and electrical performance | ✅ State of Health (SOH) | [Open-source dataset for electrical and thermal characterization of cylindrical lithium-ion batteries](https://www.sciencedirect.com/science/article/pii/S2352152X24040714) | |
| [Aitio & Howey, 2021 (Pb-acid)](https://ora.ox.ac.uk/objects/uuid:e41d3d4c-f74e-4d76-81fd-0caa77ec6cec) | Real world use. Format: System; Batteries: 1027; Measurements: Real-world | Real world use | ✔：Output Label: End of Life (EOL); State of Health (SOH) | [Predicting battery end of life from solar off-grid system field data using machine learning](https://www.sciencedirect.com/science/article/pii/S2542435121005328) | |
| [Rodríguez-Iturriaga et al, 2025 (SIB)](https://data.mendeley.com/datasets/j44rvwcpff/1) | BOL. Cell: Shenzhen Mushang Electronics NA18650-1250; Format: Cylindrical; Batteries: 2 | BOL | ✅ Discharge Capacity; Maximum Temperature Rise; Relative Discharge Time; Discharge Efficiency; Internal Resistance | [Electrical characterization of a commercial sodium-ion cell with enhanced Ragone plot analysis compared to lithium-ion cells](https://www.sciencedirect.com/science/article/pii/S2950264025000358) | |
| [Kollmeyer & Skells, 2020 (LiPoly)](https://data.mendeley.com/datasets/4fx8cjprxm/1) | BOL. Cell: Turnigy Graphene 5000mAh 65C; Batteries: 1 | BOL | ✅ State of Charge (SOC, %) | | |
| [Steinbuß et al, 2021 (n/a)](https://publikationen.bibliothek.kit.edu/1000094469) | BESS. Format: Pack; Batteries: 1 | BESS | ✅ State of Charge, SOC; State of Health, SOH| [FOBSS](https://dl.acm.org/doi/10.1145/3307772.3331020) | |
| [Lin et al, 2023 (Mixed)](https://batteryarchive.org/disruptive_list.html?t=0001) | Thermal runaway. Cell: Custom; Format: Pouch; Batteries: 55 | Thermal runaway | ✅ Thermal Runaway Severity; Thermal Runaway Occurrence; Safety Status Classification	| [Mechanically induced thermal runaway in lithium-ion batteries](https://www.sciencedirect.com/science/article/pii/S2352152X23001950) | |
| [Deng et al, 2022 (NMC-Gr)](https://github.com/BatICM/battery-charging-data-of-on-road-electric-vehicles) | EV pack data. Format: Pack; Batteries: 20 | EV pack data | ✅ Battery Capacity; Labeled Capacity | [Prognostics of battery capacity based on charging data and data-driven methods for on-road vehicles](https://www.sciencedirect.com/science/article/abs/pii/S0306261923003185) | [[Github]](https://github.com/BatICM/battery-charging-data-of-on-road-electric-vehicles) |
| [HIRF Battery Data Set](https://phm-datasets.s3.amazonaws.com/NASA/15.+HIRF+Battery+Data+Set.zip) | This dataset contains battery data collected from experiments on the Edge 540 Aircraft in a HIRF (High-Intensity Radiated Field) Chamber, providing insights into battery performance under unique testing conditions. | Battery Performance under HIRF conditions | ✅ Remaining Useful Life (RUL); State of Health (SOH); End of Discharge (EOD); Remaining Flying Time; State of Charge (SOC) | [Verification of a remaining flying time prediction system for small electric aircraft](https://papers.phmsociety.org/index.php/phmconf/article/view/2571) | |
| [Prognosis of Multivariate Battery State of Performance and Health via Transformers](https://www.materialsdatafacility.org/detail/spacetimeformer_battery_v1.2) | This dataset contains processed files for reproducing results in multivariate battery state prediction using transformers. It includes datasets for lithium-iron-phosphate fast charging and six cathode chemistries. | Multivariate Battery State Prediction | ✅ State of Health (SOH); Remaining Useful Life (RUL)；Other SOH descriptors | [Prognosis of Multivariate Battery State of Performance and Health via Transformers - Data](https://doi.org/10.18126/ckt2-g8j2) | |
| [UNIBO Powertools Dataset](https://data.mendeley.com/datasets/n6xg5fzsbv/1) | Experimental lithium-ion battery dataset released by the University of Bologna (UNIBO). The dataset contains laboratory measurements collected from 27 batteries. | Battery Modeling | ✅ State of Charge (SOC, %); SOH, State of Health | | |
| [Oxford Battery Degradation Dataset](https://data.mendeley.com/datasets/bs2j56pn7y/1) | Cycle life prediction dataset for lithium-ion batteries released by the University of Oxford. The dataset is widely used for battery degradation analysis and state-of-health estimation. | Cycle Life Prediction, SOH Estimation | ✅ LLI (Loss of Lithium Inventory); LAMPE (Loss of Active Material Positive Electrode); LAMNE (Loss of Active Material Negative Electrode); Corresponding capacity loss | | |
| [LG 18650HG2 Li-ion Battery Data](https://data.mendeley.com/datasets/cp3473x7xv/2) | Experimental dataset of LG 18650HG2 lithium-ion cells accompanied by an example deep neural network state-of-charge estimation script. | SOC Estimation | ✅ State of Charge (SOC, %); SOH, State of Health | | |
| [Real EV dataset](https://data.mendeley.com/datasets/j9ky68gnd3/1) | Real-world electric vehicle battery dataset collected from operating electric vehicles. | Real-world Battery Analysis | ✅ SOH; SOH(OCV) | | |
| [Dataset_SECL_INR21700-M50T(406辆真实运行的电动汽车电池）)](https://data.mendeley.com/datasets/mcsh4hnb8b/1) | Three real-world large-scale electric vehicle datasets from 464 EVs of 3 types, including over 1.2 million charging snippets. | Real-world EV Battery Data Analysis | ✔：Output Label: Battery Health; Battery Capacity; Anomaly Labels | | |
| [Synthetic Duty Cycles from Real-World Autonomous Electric Vehicle Driving: Accompanying Data（模拟电动网联自动驾驶汽车31个电芯测试数据）](https://doi.org/10.25740/ky011nj6376) | Collected from 20 EVs over approximately 29 months, the dataset includes charging data, labeled capacity values derived from statistical methods, and features optimized through data-driven algorithms. | Battery Capacity Prognostics | ✅ Battery Capacity; Labeled Capacity | [Battery Capacity Prognostics Dataset for On-Road Electric Vehicles](https://doi.org/10.1016/j.xcrp.2023.101536) | [[Github 14]](https://github.com/shiyunliu-battery/battery-charging-data-of-on-road-electric-vehicles) |

## 3. Materials and Chemistry

### LFP

| Dataset | Description | Task | Data Labeled or Not | Paper | Code |
| --- | --- | --- | --- | --- | --- |
| [Probability Distributed Equivalent Circuit Model](https://zenodo.org/records/10852930) | This dataset supports the development of a physically motivated voltage hysteresis model for lithium-ion batteries. The model leverages probability distributed equivalent circuits to enhance accuracy in performance predictions. | Voltage Hysteresis Modeling, Equivalent Circuit Model |❌| [Probability distributed equivalent circuit model - Data](https://doi.org/10.5281/zenodo.10852930) | |

### NMC (LiNiₓMnᵧCo₁₋ₓ₋ᵧO₂ 镍钴锰酸锂)  [三元锂电池]

| Dataset | Description | Task | Data Labeled or Not | Paper | Code |
| --- | --- | --- | --- | --- | --- |
| [Gulsoy et al, 2023 (NMC811-GrSi)](https://data.mendeley.com/datasets/pn5ct66rn5/1) | interal pressure. Cell: LG; Format: Cylindrical; Batteries: 3 |Combine raw pressure/temperature waveforms + periodic RPT capacity/resistance summary tables |✅ RPT labels | [In-situ measurement of internal gas pressure within cylindrical lithium-ion cells](https://www.sciencedirect.com/science/article/pii/S0378775323004391) | |

### 复合数据 (混合化学体系)

| Dataset | Description | Task | Data Labeled or Not | Paper | Code |
| --- | --- | --- | --- | --- | --- |
| [Cogswell et al, 2025 (NMC-Gr, Na-Ion)](https://github.com/Cogswell-Scientific-LLC/cylindrical_battery_CT_vs_SOC) | Echem and extracted geometric data (not raw CT scans). Cell: EVE 33V, Samsung 50E, HAKADI Na-Ion; Format: Cylindrical; Batteries: 3 | Echem and extracted geometric data (not raw CT scans) |✅ SOC labels | [Geometric Changes in Cylindrical Batteries as a Function of State of Charge](https://iopscience.iop.org/article/10.1149/1945-7111/ae24b3#jesae24b3s5) | [[Github]](https://github.com/Cogswell-Scientific-LLC/cylindrical_battery_CT_vs_SOC) |
| [Labor- und Feld-Batteriedatensätzen auf Zell- und Systemebene(NMC)](https://www.carl.rwth-aachen.de/cms/carl/forschung/open-source-tools-data/~btwplj/labor-und-feld-batteriedatensaetzen-auf/?lidx=1) |The processing and management of research data is a central aspect of the work at CARL. Selected research data are regularly published in conjunction with publications. Researchers are warmly invited to use this data |Multi-physics material & electrochemical characterization (static cell property testing)|❌| [Inhomogeneities and Cell-to-Cell Variations in Lithium-Ion Batteries, a Review](https://doi.org/10.3390/en14113276) | |
|[BetterBat Cell Database](https://github.com/TUMFTM/TechnoEconomicCellSelection/blob/main/inputs/CellDatabase_v6.xlsx)|Technical specifications of different battery cells. Electrochemistry, physical dimension and electrical performances are recorded|conducts quantitative performance & cost trade-off analysis to pick the optimal battery cell for electric vehicles, stationary storage, industrial equipment, etc|❌| 
|[Battery Imaging Library](https://batteryimaginglibrary.com/)|Distinctive features include the release of raw experimental data (radiographs, sinograms, X-ray and electron diffraction patterns) together with rare operando and multi-resolution datasets|test models on defect types, from nanoscale cracks (seen in SEM, TEM) to micron-scale structural issues (seen in X-ray CT), and even chemical inhomogeneities (detected by EDS, XANES-CT)|❌|[Battery Imaging Library: Multi-length scale and multi-modal synchrotron and laboratory battery imaging data for all](https://doi.org/10.26434/chemrxiv-2025-sbp73)||

### 其他未明确归类的数据集

| Dataset | Description | Task | Data Labeled or not | Paper | Code |
| --- | --- | --- | --- | --- | --- |
| []() | RAGflow frame | | | | [[Github 9]](https://github.com/infiniflow/ragflow) |


# 锂离子电池相关论文汇总

| Paper | Task | Journal | Authors | Date | Dataset/Github |
| --- | --- | --- | --- | --- | --- |
| [Agent-in-the-loop to distill expert knowledge into artificial intelligence models: a survey](https://link.springer.com/article/10.1007/s10462-025-11255-1) | 综述：将专家知识蒸馏到人工智能模型中的方法与路径 | *Artificial Intelligence Review* | Jiayuan Gao, Yingwei Zhang, Yiqiang Chen, et al. | 2025年 | --- |
| [Li-Ion Battery Doctor: A Fine-Tuned and Explainable Large-Language Model for Health Prognosis](https://ieeexplore.ieee.org/document/11340691) | 微调且可解释的大语言模型，用于锂电池健康状态预测 | *IEEE Transactions on Energy Conversion* | Rudai Yan, Lingzhi Su, Yan Xu | 2026年1月12日 | https://www.batteryarchive.org/cycle_list.html?time=0001|
| [LiBrain: LLM-Powered Li-ion Battery Diagnostics with Time-Series-Aware Retrieval-Augmented Framework for E-bikes](https://ojs.aaai.org/index.php/AAAI/article/view/41439) | 基于时序感知检索增强框架（RAG）的 LLM，用于电动自行车锂电池诊断 | *Proceedings of the AAAI Conference on Artificial Intelligence (AAAI 2026)* | Shanshan Huang, Jing Jiang, Peng Cai, Qiwen Dong, Huiqi Hu, et al. | 2026年 | --- |
| [Dual-Scale Nonstationary Representation for Degradation Tracking and Aging-Informed Monitoring of Lithium-Ion Battery System](https://ieeexplore.ieee.org/document/11368627) | 双尺度非平稳表示方法，用于退化跟踪与老化感知监测 | *IEEE Transactions on Industrial Electronics* | Jiayang Yang, Chunhui Zhao | 2026年1月29日 | https://zenodo.org/records/18158360(20260725暂未公开) |
| [TimeSeries2Report prompting enables adaptive large language model management of lithium-ion batteries](https://arxiv.org/abs/2512.16453) | 通过提示工程实现自适应 LLM 的锂电池管理 | **arXiv 预印本** (arXiv:2512.16453, v2) <br>  | Jiayang Yang, Chunhui Zhao, Martin Guay, Zhixing Cao | 2025年12月提交，2026年1月修订 | https://zenodo.org/records/18158360(20260725暂未公开) https://data.mendeley.com/datasets/nsc7hnsg4s/2 https://data.matr.io/1/projects/5c48dd2bc625d700019f3204 |
| [Real-time personalized health status prediction of lithium-ion batteries using deep transfer learning](https://pubs.rsc.org/ee/article/15/10/4083/767199/Real-time-personalized-health-status-prediction-of) | 利用深度迁移学习实现锂电池实时个性化健康状态预测 | *Energy & Environmental Science* | Guijun Ma, Songpei Xu, Benben Jiang, Cheng Cheng, Xin Yang, Yue Shen, Tao Yang, Yunhui Huang, Han Ding, Ye Yuan | 2022年7月30日 |[Mendeley (nsc7hnsg4s/2)](https://data.mendeley.com/datasets/nsc7hnsg4s/2) <br> [Zenodo (10.5281/zenodo.6827566)](https://doi.org/10.5281/zenodo.6827566) |
| [LiPM Foundation Model for Lithium-Ion Battery Analysis](https://dl.acm.org/doi/10.1145/3711896.3737027) | 面向锂离子电池分析的基础模型（Foundation Model） | *Proceedings of the 31st ACM SIGKDD Conference (KDD '25)* | Juren Li, Yang Yang, Hanchen Su, Jiayu Liu, Youmin Chen, Jianfeng Zhang, Lujia Pan | 2025年8月3日 | https://github.com/JuRenGithub/LiPM |

# 锂离子电池论文中的评价方法

| object | method | paper |
| --- | --- | --- |
| Anomaly, bulging and internal short-circuit (ISC) detection | Precision（精确率）和 Recall（召回率） | [LiBrain: LLM-Powered Li-ion Battery Diagnostics with Time-Series-Aware Retrieval-Augmented Framework for E-bikes](https://ojs.aaai.org/index.php/AAAI/article/view/41439) |
| Remaining range, State of Health (SOH) and Remaining Useful Life (RUL) prediction | MAE（Mean Absolute Error，平均绝对误差）和 MSE（Mean Squared Error，均方误差） | [LiBrain: LLM-Powered Li-ion Battery Diagnostics with Time-Series-Aware Retrieval-Augmented Framework for E-bikes](https://ojs.aaai.org/index.php/AAAI/article/view/41439) |
| Real-world diagnostic recommendation effectiveness | Adoption Rate（采用率）：$1-\frac{\text{non-adopted recommendations}}{\text{total recommendations}}$ | [LiBrain: LLM-Powered Li-ion Battery Diagnostics with Time-Series-Aware Retrieval-Augmented Framework for E-bikes](https://ojs.aaai.org/index.php/AAAI/article/view/41439) |
| Contribution of individual framework components | Ablation study（消融实验）：完整模型分别与移除 LLiM、移除知识库以及仅使用 LLM 的变体比较 | [LiBrain: LLM-Powered Li-ion Battery Diagnostics with Time-Series-Aware Retrieval-Augmented Framework for E-bikes](https://ojs.aaai.org/index.php/AAAI/article/view/41439) |
| State of Charge (SOC) prediction | RMSE（Root Mean Squared Error，均方根误差）和 MAE；预测第 100 分钟的系统平均 SOC，并与真实值比较 | [TimeSeries2Report prompting enables adaptive large language model management of lithium-ion batteries](https://arxiv.org/abs/2512.16453) |
| Factual consistency of generated battery reports | FactScore：独立评判 LLM 按属性给出 1（高度一致）、0.5（部分一致）或 0（低一致），再对全部属性得分取平均 | [TimeSeries2Report prompting enables adaptive large language model management of lithium-ion batteries](https://arxiv.org/abs/2512.16453) |
| Statistical significance of report-quality improvement | 均值与 95% CI（置信区间）；使用单侧配对 Wilcoxon 检验计算 $p$ 值 | [TimeSeries2Report prompting enables adaptive large language model management of lithium-ion batteries](https://arxiv.org/abs/2512.16453) |
| Abnormality detection in LIB operation monitoring | Accuracy（Acc，准确率）和 False Alarm Rate（FAR，误报率）；预测结果与专家标注的 ground truth 比较 | [TimeSeries2Report prompting enables adaptive large language model management of lithium-ion batteries](https://arxiv.org/abs/2512.16453) |
| Personalized capacity prediction | RMSE（单位：mAh）、$R^2$（决定系数）和 MAPE（Mean Absolute Percentage Error，平均绝对百分比误差） | [Real-time personalized health status prediction of lithium-ion batteries using deep transfer learning](https://pubs.rsc.org/en/content/articlelanding/2022/ee/d2ee01676a) |
| Remaining Useful Life (RUL) prediction | RMSE（单位：cycles）、$R^2$ 和 MAPE | [Real-time personalized health status prediction of lithium-ion batteries using deep transfer learning](https://pubs.rsc.org/en/content/articlelanding/2022/ee/d2ee01676a) |
| Robustness to the number of input and sampled cycles | 用不同输入循环数与采样循环数组合构成敏感性实验，并以 RMSE 矩阵/热图比较预测误差 | [Real-time personalized health status prediction of lithium-ion batteries using deep transfer learning](https://pubs.rsc.org/en/content/articlelanding/2022/ee/d2ee01676a) |
| RUL, SOH, discharge-capacity change ($\Delta Q_D$), charge-capacity change ($\Delta Q_C$) and internal resistance (IR) prediction | MSE 和 MAE；在多个下游回归任务上分别报告，以衡量预测值与真实值的偏差 | [LiPM Foundation Model for Lithium-Ion Battery Analysis](https://dl.acm.org/doi/10.1145/3711896.3737027) |

# Awesome Lithium-Ion Battery Resources
## 目录

- [收录规则](#收录规则)
- [物理模型与仿真代码](#物理模型与仿真代码)
- [参数辨识、状态估计与数字孪生](#参数辨识状态估计与数字孪生)
- [机器学习与基础模型](#机器学习与基础模型)
- [电化学数据分析](#电化学数据分析)
- [实验设备、文件解析与接口代码](#实验设备文件解析与接口代码)
- [微观结构、成像与扫描数据](#微观结构成像与扫描数据)
- [图像重建、分割与微结构分析](#图像重建分割与微结构分析)
- [安全、热失控与事故数据](#安全热失控与事故数据)
- [BMS、固件、开源硬件与通信](#bms固件开源硬件与通信)
- [材料数据库、知识图谱与 API](#材料数据库知识图谱与-api)
- [数据标准、本体与电池护照](#数据标准本体与电池护照)
- [制造、成本、回收与生命周期](#制造成本回收与生命周期)
- [测试标准与法规入口](#测试标准与法规入口)
- [推荐的仓库结构](#推荐的仓库结构)
- [贡献模板](#贡献模板)

## 收录规则

- 优先收录可公开访问的原始数据、官方代码仓库、项目主页、标准机构页面和论文落地页。
- `开放` 表示无需购买即可访问；`需注册` 表示免费账户或 API key；`商业` 表示可能需要许可证或付费。
- GitHub 上的代码并不自动等于可自由再分发；使用前必须检查仓库中的 `LICENSE`。
- 数据应同时记录许可证、版本、DOI、化学体系、规格、测试条件、文件格式和引用方式。
- 本目录是持续维护的索引，不声称在任何时间点穷尽整个互联网。失效链接、重复记录和许可证变化应通过 Issue/PR 更新。


## 物理模型与仿真代码

### 电芯电化学、热与老化模型

| 名称 | 链接 | 语言/平台 | 模型与用途 | 开放性 |
| --- | --- | --- | --- | --- |
| PyBaMM | [GitHub](https://github.com/pybamm-team/PyBaMM) · [Docs](https://docs.pybamm.org/) | Python | SPM、SPMe、DFN、电热耦合、降解与参数集 | BSD-3-Clause |
| liionpack | [GitHub](https://github.com/pybamm-team/liionpack) | Python | 基于 PyBaMM 的串并联电池包仿真 | 开源 |
| PyBOP | [GitHub](https://github.com/pybop-team/PyBOP) | Python | 物理模型参数辨识、优化与不确定性分析 | 开源 |
| SLIDE | [GitHub](https://github.com/Battery-Intelligence-Lab/SLIDE) | C++ | 高速电化学、热、老化及电池包仿真 | 开源 |
| PETLION | [GitHub](https://github.com/MarcBerliner/PETLION.jl) | Julia | 毫秒级多孔电极模型 | 开源 |
| LIONSIMBA | [GitHub](https://github.com/lionsimbatoolbox/LIONSIMBA) | MATLAB | P2D/DFN 电化学模型 | 开源代码；需 MATLAB |
| MPET | [GitHub](https://github.com/TRI-AMDD/mpet) | Python | 多相多孔电极理论 | 开源 |
| MPET Network | [GitHub](https://github.com/Ombrini/MPET_Network) | Python | MPET 网络及电芯级扩展 | 开源 |
| BattMo | [GitHub](https://github.com/BattMoTeam/BattMo) · [Docs](https://battmoteam.github.io/BattMo/) | MATLAB | 1D/2D/3D 连续介质电化学—热耦合 | GPL-3.0；需 MATLAB |
| DandeLiion | [Web solver](https://www.dandeliion.com/) | Web/C++ 后端 | 快速 Newman/DFN 与 3D 热耦合模型 | 免费 Web 服务；商业使用需核对 |
| Dualfoil | [Project](https://www.cchem.berkeley.edu/jsngrp/fortran.html) | Fortran | 经典 Doyle–Fuller–Newman 模型代码 | 旧版研究代码 |
| Thevenin | [GitHub](https://github.com/NREL/thevenin) | Python | 等效电路与热模型 | 开源 |
| BLAST-Lite | [GitHub](https://github.com/NREL/BLAST-Lite) | Python | 经验老化、寿命与应用工况仿真 | 开源 |
| COBRAPRO | [GitHub](https://github.com/COBRAPROsimulator/COBRAPRO) | MATLAB | 电化学模型与参数优化 | 开源代码；需 MATLAB |
| batP2dFoam | [GitHub](https://github.com/redyxg/batP2dFoam) | C++/OpenFOAM | 基于 OpenFOAM 的 P2D 电池仿真 | 开源 |
| Simscape Battery Library | [GitHub](https://github.com/WDWidanage/Simscape-Battery-Library) | MATLAB/Simscape | 电芯及电池包多域模型 | 代码公开；需商业软件 |
| CellModels | [GitHub](https://github.com/mjlacey/cellmodels) | Julia | 电芯性能与电池包模型 | 开源 |
| ECStoolbox | [BMS Algorithms](http://mocha-java.uccs.edu/BMS1/index.html) | MATLAB | ECM、热模型、Kalman 滤波教学实现 | 免费下载；需 MATLAB |
| Battery Design Studio examples | [Faraday workbook](https://www.faraday.ac.uk/fi-cell-modelling-workbook/) | Excel | 电芯设计、性能与平衡教学工作簿 | 免费下载 |
| OpenFOAM | [Project](https://openfoam.org/) | C++ | 冷却、流体、传热和热失控 CFD 的通用基础 | GPL |

### 电池包、系统与成本模型

| 名称 | 链接 | 语言/平台 | 用途 | 开放性 |
| --- | --- | --- | --- | --- |
| BatPaC | [Argonne](https://www.anl.gov/partnerships/batpac-battery-manufacturing-cost-estimation) | Excel | 电芯/电池包设计、性能与制造成本 | 免费下载；需查看许可 |
| Back of the Battery | [GitHub](https://github.com/ndrewwang/BotB) | Python | 电芯选择、电池包性能与成本 | 开源 |
| Cell Simulator | [Paper/tool](https://pubs.rsc.org/en/content/articlelanding/2020/mh/d0mh00067a) | Excel | 电芯与电池包设计权衡 | 附件开放性依论文页 |
| ISEA Cell and Pack Database | [GitLab](https://git.rwth-aachen.de/isea/isea-cell-and-pack-database) | MATLAB | 电芯参数、包级性能与选型 | 开源/需核对数据许可 |
| oemof.solph | [GitHub](https://github.com/oemof/oemof-solph) | Python | 含储能的能源系统优化 | 开源；非电池专用 |
| PyPSA | [GitHub](https://github.com/PyPSA/PyPSA) | Python | 电力系统与储能规划/运行 | MIT；非电池专用 |

## 参数辨识、状态估计与数字孪生

| 名称 | 链接 | 语言 | 主要能力 | 备注 |
| --- | --- | --- | --- | --- |
| AutoSOH / moirae | [GitHub](https://github.com/ROVI-org/auto-soh) | Python | 在线 ECM 参数、SOC/SOH 状态估计与 Kalman 滤波 | 开源 |
| BatEst | [GitHub](https://github.com/Battery-Intelligence-Lab/BatEst) | MATLAB | 低阶模型仿真与参数估计 | 开源代码；需 MATLAB |
| PyBOP | [GitHub](https://github.com/pybop-team/PyBOP) | Python | 基于 PyBaMM 的参数优化、似然与辨识 | 开源 |
| impedance.py | [GitHub](https://github.com/ECSHackWeek/impedance.py) | Python | EIS 等效电路拟合与验证 | MIT |
| EISFitting | [GitHub](https://github.com/Samuel-Buteau/EISFitting) | Python | EIS 等效电路参数拟合 | 开源 |
| Thevenin | [GitHub](https://github.com/NREL/thevenin) | Python | ECM/热模型，可用于估计器和数字孪生 | 开源 |
| MathWorks battery modeling examples | [GitHub](https://github.com/mathworks/battery-modeling-solutions-with-simscape-and-measured-data) | MATLAB/Simulink | ECM、参数估计、包模型、平衡与 RUL 示例 | 代码公开；需商业工具箱 |

## 机器学习与基础模型

| 名称 | 链接 | 语言 | 任务 | 备注 |
| --- | --- | --- | --- | --- |
| BatteryML | [GitHub](https://github.com/microsoft/BatteryML) | Python/PyTorch | 数据预处理、特征工程、SOH/RUL/寿命基准 | MIT |
| BatteryLife | [GitHub](https://github.com/Ruifeng-Tan/BatteryLife) | Python | 多数据集寿命预测与 18 类基准模型 | 开放数据与代码 |
| BEEP | [GitHub](https://github.com/TRI-AMDD/beep) | Python | 循环数据结构化、特征提取、早期寿命预测 | BSD-3-Clause |
| LiPM | [GitHub](https://github.com/JuRenGithub/LiPM) | Python | 电池时序基础模型，下游 SOH/RUL/容量/内阻任务 | 以仓库许可为准 |
| MambaLithium | [GitHub](https://github.com/zshicode/MambaLithium) | Python/PyTorch | SOC、SOH、RUL 的状态空间模型 | 研究代码 |
| Battery RUL Estimation | [GitHub](https://github.com/MichaelBosello/battery-rul-estimation) | Python/Keras | 基于深度 LSTM 的 RUL 示例 | 研究代码 |
| NASA Prognostics Algorithms Library | [GitHub](https://github.com/nasa/PrognosticsAlgorithmLibrary) | MATLAB | 通用 PHM/RUL 算法，可用于电池 | NASA 开源 |
| NASA Prognostics Models | [GitHub](https://github.com/nasa/prog_models) | Python | 状态传播、事件与剩余寿命预测框架 | NASA 开源 |

> 建议：对 AI 仓库同时记录训练/测试电芯是否泄漏、跨电芯与跨化学体系划分、输入循环数、随机种子、评价指标和权重许可证，避免只收录“能运行的 notebook”。

## 电化学数据分析

| 名称 | 链接 | 语言 | 用途 | 备注 |
| --- | --- | --- | --- | --- |
| PyProBE | [GitHub](https://github.com/ImperialCollegeLondon/PyProBE) | Python | 电池测试数据处理、容量/能量/增量容量等分析 | 开源 |
| cellpy | [GitHub](https://github.com/jepegit/cellpy) | Python | 循环数据读取、清洗、汇总和绘图 | MIT |
| Ampworks | [GitHub](https://github.com/NREL/ampworks) | Python | 测试数据指标提取 | 开源 |
| Battery Data Toolkit | [GitHub](https://github.com/ROVI-org/battery-data-toolkit) | Python | 标准化电池数据与特征提取 | 开源 |
| DiffCapAnalyzer | [GitHub](https://github.com/nicolet5/DiffCapAnalyzer) | Python/Dash | dQ/dV 清洗、峰值定量与交互可视化 | 开源 |
| impedance.py | [GitHub](https://github.com/ECSHackWeek/impedance.py) | Python | Nyquist/Bode、ECM 拟合与验证 | MIT |
| pyDRTtools | [GitHub](https://github.com/ciuccislab/pyDRTtools) | Python | 弛豫时间分布（DRT）分析与界面 | 开源 |
| DRTtools | [GitHub](https://github.com/ciuccislab/DRTtools) | MATLAB | DRT 分析 | 开源代码；需 MATLAB |
| hybrid-drt | [GitHub](https://github.com/jdhuang-csm/hybrid-drt) | Python | DRT-DOP 联合模型 | 开源 |
| ALawa | [Project](https://www.hnei.hawaii.edu/alawa/) | MATLAB | 退化模式分析（DVA/ICA） | 免费下载；需 MATLAB |
| ixdat | [GitHub](https://github.com/ixdat/ixdat) | Python | 电化学及联用实验数据模型与分析 | MIT |
| echemdb | [GitHub](https://github.com/echemdb/echemdb) | Python/CSV | FAIR 电化学数据发布与处理 | 开源 |

## 实验设备、文件解析与接口代码

| 名称 | 链接 | 语言 | 设备/格式 | 功能 |
| --- | --- | --- | --- | --- |
| BattETL | [GitHub](https://github.com/BattGenie/battetl) | Python | Arbin、Maccor | 提取、转换并写入数据库 |
| Battery Data Format | [GitHub](https://github.com/battery-data-alliance/battery-data-format) | Python/Parquet | 通用；含 Neware 适配 | 标准数据结构、转换与验证 |
| NewareNDA | [GitHub](https://github.com/Solid-Energy-Systems/NewareNDA) | Python | Neware `.nda/.ndax` | 读取与转换 |
| yadg | [GitHub](https://github.com/dgbowl/yadg) | Python | 多类电化学/实验文件 | 自动解析为统一数据结构 |
| galvani | [GitHub](https://github.com/echemdata/galvani) | Python | BioLogic、Arbin | 二进制/导出文件解析 |
| eclabfiles | [GitHub](https://github.com/vetschn/eclabfiles) | Python | BioLogic EC-Lab | `.mpr` 等文件解析 |
| Aurora BioLogic | [GitHub](https://github.com/EmpaEconversion/aurora-biologic) | Python | BioLogic | 控制通道、加载协议、启停实验 |
| Aurora Cycler Manager | [GitHub](https://github.com/EmpaEconversion/aurora-cycler-manager) | Python | 多电池测试设备 | 自动化调度、数据库和监控 |
| PyGamry | [GitHub](https://github.com/jdhuang-csm/pygamry) | Python | Gamry | 仪器控制与数据采集 |
| PyMacNet | [GitHub](https://github.com/battery-data-alliance/pymacnet) | Python | Maccor | 网络接口与数据抓取 |
| PyCTIArbin | [GitHub](https://github.com/battery-data-alliance/pyctiarbin) | Python | Arbin | CTI 自动化接口 |
| galv | [GitHub organization](https://github.com/galv-team) | Python | 多类 cycler | 采集、同步、数据管理与 API |
| Voltaiq Data Format | [GitHub](https://github.com/SubwayLabs/VoltaiqDataFormat) | Python | 通用 | Voltaiq 开放数据格式工具 |
| Universal Battery Database | [GitHub](https://github.com/Samuel-Buteau/universal-battery-database) | Python | 通用 | 电池测试数据库模式与处理 |
| DATTES | [GitLab](https://gitlab.com/dattes/dattes/) | MATLAB | 多类 cycler | 数据处理、评价与可视化 |
| AmpLabs | [GitHub](https://github.com/battery-data-alliance/amplabs) | Python/MATLAB | 实验室数据 | 数据管理与分析 |
| datalab | [Docs](https://docs.datalab-org.io/) | Python/Web | 通用实验室 | ELN/LIMS、样品和实验数据管理 |
| PyVISA | [GitHub](https://github.com/pyvisa/pyvisa) | Python | VISA/SCPI 仪器 | 通用电源、负载和测量设备接口 |
| python-can | [GitHub](https://github.com/hardbyte/python-can) | Python | CAN | BMS/CAN 总线读写与记录 |
| cantools | [GitHub](https://github.com/cantools/cantools) | Python | CAN/DBC | DBC 编解码、日志转换与绘图 |
| pymodbus | [GitHub](https://github.com/pymodbus-dev/pymodbus) | Python | Modbus | BMS、充电器、逆变器接口基础库 |
| Eclipse Mosquitto | [Project](https://mosquitto.org/) | C/MQTT | MQTT | BMS/实验室遥测消息代理 |

## 微观结构、成像与扫描数据

| 名称 | 链接 | 模态/内容 | 用途 | 访问 |
| --- | --- | --- | --- | --- |
| Battery Imaging Library | [Portal](https://batteryimaginglibrary.com/) | SEM、EDS、EBSD、XCT、XANES-CT 等 | 跨尺度电池成像数据检索与下载 | 开放 |
| NREL Battery Microstructures Library | [Portal](https://www.nrel.gov/transportation/microstructure) | NMC/石墨电极灰度与分割 3D X-ray CT | 孔隙率、曲折度、微结构模型 | 开放 |
| Glimpse CT Dataset | [Figshare](https://plus.figshare.com/articles/dataset/A_dataset_of_over_one_thousand_computed_tomography_scans_of_battery_cells/25330501) | 超过一千个电芯 CT 扫描 | 电芯缺陷、结构和质量检测 | 开放/依记录许可 |
| Glimpse Viewer | [Web app](https://app.glimp.se/) | 电芯 X-ray CT 在线交互 | 快速浏览与演示 | 免费 Web |
| Battery Failure Databank Imaging | [NREL/NLR](https://www.nrel.gov/transportation/battery-failure) | 高速 X-ray radiography + 热失控数据 | 失效机理与安全基准 | 开放 |

## 图像重建、分割与微结构分析

### CT/断层重建与三维可视化

| 名称 | 链接 | 语言/平台 | 主要能力 | 开放性 |
| --- | --- | --- | --- | --- |
| TomoPy | [GitHub](https://github.com/tomopy/tomopy) | Python | 投影预处理、相位恢复、伪影去除、CT 重建 | BSD-3-Clause |
| ASTRA Toolbox | [Project](https://astra-toolbox.com/) | Python/MATLAB/CUDA | 高性能 2D/3D 投影和迭代重建 | GPL |
| TIGRE | [GitHub](https://github.com/CERN/TIGRE) | Python/MATLAB/CUDA | GPU 迭代 CT/CBCT 重建 | BSD |
| Core Imaging Library (CIL) | [GitHub](https://github.com/TomographicImaging/CIL) | Python | CT 数据读取、优化和重建流水线 | Apache-2.0 |
| nDTomo | [GitHub](https://github.com/antonyvam/nDTomo) | Python | 高维 X-ray 谱学、化学成像与断层 | 开源 |
| tomosipo | [GitHub](https://github.com/ahendriksen/tomosipo) | Python/ASTRA | 可微分断层算子与重建 | 开源 |
| Fiji/ImageJ | [Project](https://imagej.net/software/fiji/) | Java/GUI | 图像预处理、配准、分割与 3D 插件生态 | GPL |
| napari | [GitHub](https://github.com/napari/napari) | Python/GUI | n 维图像浏览、标注和插件 | BSD |
| 3D Slicer | [Project](https://www.slicer.org/) | C++/Python/GUI | 3D 分割、配准与可视化 | BSD-style |
| ParaView | [Project](https://www.paraview.org/) | C++/Python/GUI | 大规模 3D 场和网格可视化 | BSD |
| tomviz | [GitHub](https://github.com/OpenChemistry/tomviz) | C++/Python/GUI | 材料断层重建与可视化 | BSD |

### 孔结构、分割和有效性质

| 名称 | 链接 | 语言 | 主要能力 | 开放性 |
| --- | --- | --- | --- | --- |
| TauFactor | [GitHub](https://github.com/tldr-group/taufactor) | Python/GPU | 相体积分数、曲折度和有效传输性质 | 开源 |
| PoreSpy | [GitHub](https://github.com/PMEAL/porespy) | Python | 多孔介质图像生成、过滤、网络提取与指标 | MIT |
| OpenPNM | [GitHub](https://github.com/PMEAL/OpenPNM) | Python | 孔网络建模、传输与反应模拟 | MIT |
| MATBOX | [GitHub](https://github.com/NREL/MATBOX_Microstructure_analysis_toolbox) | MATLAB | 微结构分割、表征、网格化和生成 | 开源代码；需 MATLAB |
| scikit-image | [GitHub](https://github.com/scikit-image/scikit-image) | Python | 通用去噪、阈值、形态学和分割 | BSD |
| ilastik | [Project](https://www.ilastik.org/) | GUI/Python | 交互式机器学习像素/对象分类 | GPL |
| Cellpose | [GitHub](https://github.com/MouseLand/cellpose) | Python/PyTorch | 通用深度学习分割，可迁移到颗粒/孔隙 | BSD；非电池专用 |

### SEM/TEM/EDS/EBSD/衍射与谱学

| 名称 | 链接 | 语言 | 主要能力 | 开放性 |
| --- | --- | --- | --- | --- |
| HyperSpy | [GitHub](https://github.com/hyperspy/hyperspy) | Python | 多维显微与谱学数据、EDS/EELS | GPL |
| pyxem | [GitHub](https://github.com/pyxem/pyxem) | Python | 4D-STEM、电子衍射、取向和应变分析 | GPL-3.0 |
| LiberTEM | [GitHub](https://github.com/LiberTEM/LiberTEM) | Python | 大规模像素化 STEM 分布式分析 | GPL |
| py4DSTEM | [GitHub](https://github.com/py4dstem/py4DSTEM) | Python | 4D-STEM 数据处理与分析 | GPL |
| Atomap | [GitHub](https://github.com/atomap-dev/atomap) | Python | 原子分辨 STEM 晶格与原子柱定量 | GPL-3.0 |
| AtomAI | [GitHub](https://github.com/pycroscopy/atomai) | Python/PyTorch | 显微图像和谱学的深度学习分析 | MIT |
| pyFAI | [GitHub](https://github.com/silx-kit/pyFAI) | Python | 2D X-ray 衍射方位积分 | MIT |
| GSAS-II | [Project](https://advancedphotonsource.github.io/GSAS-II-tutorials/) | Python/GUI | 粉末/单晶衍射分析和 Rietveld 精修 | 开放 |
| pymatgen-analysis-diffraction | [Docs](https://pymatgen.org/pymatgen.analysis.diffraction.html) | Python | XRD/中子/电子衍射图样计算 | MIT |

## 安全、热失控与事故数据

| 名称 | 链接 | 数据内容 | 尺度 | 访问说明 |
| --- | --- | --- | --- | --- |
| Battery Failure Databank | [NREL/NLR](https://www.nrel.gov/transportation/battery-failure) | 针刺、加热、内短路；热量、抛射质量、高速 X-ray | 电芯 | 开放 |
| Sandia Energy Storage Safety R&D Repository | [Repository](https://www.sandia.gov/energystoragesafety/rd-data-repository/) | ARC、老化后安全、热失控和表征原始数据 | 电芯/系统 | 开放 |
| EPRI BESS Failure Incident Database | [Database](https://storagewiki.epri.com/index.php/BESS_Failure_Event_Database) | 全球储能系统事故、化学体系、规模、场景和来源 | 系统 | 开放，提供 CSV |
| UL FSRI UL 9540A experimental data | [Zenodo](https://zenodo.org/records/7244850) | 电芯与集装箱式 BESS 热失控、热释放和气体测量 | 电芯/安装级 | 开放 |
| UL FSRI Materials and Products Database | [Database](https://materials.fsri.org/) | 火灾材料性质、点火和燃烧测试 | 材料/产品 | 免费 Web |
| FAA Lithium Battery Incidents | [Database](https://www.faa.gov/hazmat/resources/lithium_batteries/incidents) | 航空运输中冒烟、起火和极端发热事件 | 事故 | 开放、持续更新 |
| CPSC e-bike battery testing report | [PDF](https://www.cpsc.gov/s3fs-public/CPSC-Staff-Statement-on-e-Bike-Battery-Testing-and-Exponent-Report.pdf) | 电动自行车电池包测试与安全表现 | 电池包 | 开放报告 |
| Tunnel EV fire dataset | [Data article](https://www.sciencedirect.com/science/article/pii/S2352340922010423) | 隧道环境中的电动汽车火灾实验 | 车辆 | 依文章附件许可 |
| Full-scale BESS fire test dataset | [Data article](https://www.sciencedirect.com/science/article/pii/S2352340922009167) | 全尺度储能系统火灾测量 | 系统 | 依文章附件许可 |
| Thermal runaway in air and oil | [Data article](https://www.sciencedirect.com/science/article/pii/S2352340919307334) | 不同环境下的热失控实验 | 电芯 | 依文章附件许可 |
| Battery safety data on Battery Archive | [Portal](https://www.batteryarchive.org/) | 多来源机械诱发热失控及循环数据 | 电芯 | 开放/依条目许可 |

> 安全数据使用提示：事故数据库不能直接替代受控实验；比较前应统一 SOC、SOH、化学体系、容量、触发方式、环境、量热边界、是否计入抛射物和采样频率。

## BMS、固件、开源硬件与通信

| 名称 | 链接 | 平台/语言 | 范围 | 开放性/状态 |
| --- | --- | --- | --- | --- |
| foxBMS 2 | [GitHub](https://github.com/foxBMS/foxbms-2) · [Docs](https://docs.foxbms.org/) | STM32/C/Python | 模块化高压 BMS，硬件、固件、测试和工具链 | 软件 BSD-3-Clause；硬件/文档 CC-BY-4.0 |
| Libre Solar BMS Firmware | [GitHub](https://github.com/LibreSolar/bms-firmware) | Zephyr RTOS/C | bq769x0/bq769x2/ISL94202 BMS 固件 | Apache-2.0 |
| Libre Solar BMS C1 | [GitHub](https://github.com/LibreSolar/bms-c1) | KiCad | 16S/100A 开源 BMS 硬件 | 开放硬件 |
| Libre Solar BMS 8S50-IC | [GitHub](https://github.com/LibreSolar/bms-8s50-ic) | KiCad | 12–24 V 集成式 BMS | 开放硬件 |
| ENNOID-BMS | [GitHub](https://github.com/EnnoidMe/ENNOID-BMS) | STM32/C/KiCad | 主从式高压 BMS、CAN、被动均衡 | 开源；项目较旧 |
| ENNOID-BMS Tool | [GitHub](https://github.com/EnnoidMe/ENNOID-BMS-Tool) | C++/Qt | 参数配置、监控和固件升级 | 开源 |
| diyBMS v4 | [Hardware](https://github.com/stuartpittaway/diyBMSv4) · [Firmware](https://github.com/stuartpittaway/diyBMSv4Code) | ESP/AVR/C++ | 模块化 DIY 电池监控与均衡 | 开源；自行承担安全责任 |
| SimpBMS | [GitHub](https://github.com/Tom-evnut/SimpBMS) | Arduino/C++ | 复用 Tesla 电池模块监控板的 BMS 控制 | 社区项目 |
| dbus-serialbattery | [GitHub](https://github.com/Louisvdw/dbus-serialbattery) | Python | 多品牌串口 BMS 接入 Victron VenusOS | 开源 |
| bms-to-inverter | [GitHub](https://github.com/ai-republic/bms-to-inverter) | Java | UART/RS485/Modbus/CAN 的 BMS—逆变器协议桥 | 开源 |
| OpenDTU-OnBattery | [GitHub](https://github.com/hoylabs/OpenDTU-OnBattery) | ESP32/C++ | BMS、逆变器、充电器、MQTT 集成 | 开源 |
| python-can | [GitHub](https://github.com/hardbyte/python-can) | Python | CAN 总线接入、记录和测试 | 开源基础库 |
| cantools | [GitHub](https://github.com/cantools/cantools) | Python | DBC、CAN 编解码和日志分析 | MIT |
| SavvyCAN | [GitHub](https://github.com/collin80/SavvyCAN) | C++/Qt | CAN 抓包、DBC、回放和逆向分析 | MIT |

> 警告：开源 BMS 代码不能替代电气隔离、接触器失效分析、ASIL/功能安全、EMC、过流保护、熔断器、热设计和认证测试。不要将研究原型直接用于道路车辆或高压储能系统。

## 材料数据库、知识图谱与 API

| 名称 | 链接 | 接口 | 电池相关内容 | 访问说明 |
| --- | --- | --- | --- | --- |
| Materials Project Battery Explorer | [Explorer documentation](https://docs.materialsproject.org/apps/explorer-apps/battery-explorer) | Web | 插层电极、电压、容量、稳定性 | 免费账户 |
| Materials Project API | [Docs](https://docs.materialsproject.org/downloading-data/using-the-api/getting-started) · [GitHub](https://github.com/materialsproject/api) | REST/Python | insertion electrodes、电解液分子、结构与热力学 | API key/依条款 |
| pymatgen | [GitHub](https://github.com/materialsproject/pymatgen) | Python | 相图、扩散、界面、结构与电极分析 | MIT |
| OQMD | [API](https://www.oqmd.org/api/) | REST/OPTIMADE | 开放量子材料结构与热力学数据 | CC-BY-4.0，无需凭据 |
| NOMAD | [Portal](https://nomad-lab.eu/) · [API](https://nomad-lab.eu/prod/v1/api/v1/extensions/docs) | REST/OPTIMADE | 计算与实验材料数据、工作流和原始文件 | 开放/账户功能混合 |
| OPTIMADE | [Specification](https://www.optimade.org/specification/latest/) · [Providers](https://www.optimade.org/providers-dashboard/) | 标准 REST API | 跨 Materials Project、OQMD、NOMAD 等检索结构 | 开放标准 |
| AFLOW | [API](https://aflow.org/API/aflux/) | REST/AFLUX | 计算材料性质与晶体结构 | 依 AFLOW 条款 |
| Crystallography Open Database | [Portal](https://www.crystallography.net/cod/) | Web/SQL/OPTIMADE | 实验晶体结构 CIF | 开放 |
| Materials Cloud | [Portal](https://www.materialscloud.org/) · [OPTIMADE](https://optimade.materialscloud.org/) | Web/REST | 计算材料数据与可重复工作流 | 开放/依记录许可 |
| PubChem PUG REST | [Docs](https://pubchem.ncbi.nlm.nih.gov/docs/pug-rest) | REST | 电解液溶剂、盐、添加剂的化学与安全信息 | 开放 |
| TUM Battery Cell Database | [Zenodo](https://zenodo.org/records/10604028) · [Code](https://github.com/TUMFTM/TechnoEconomicCellSelection) | 文件/Python | 商用电芯规格与技术经济选型 | 开放/依记录许可 |
| About:Energy Voltt | [Cell Library](https://voltt.aboutenergy.io/cell-library) | Web | 商用电芯参数与模型目录 | 免费浏览/商业数据混合 |
| Batemo Cell Explorer | [Portal](https://www.batemo.com/products/batemo-cell-explorer/) | Web | 商用电芯性能与模型可视化 | 免费浏览/商业模型 |
| Battery Knowledge Graph | [Portal](https://battery.knowledge-graph.eu/) | Web/Linked Data | 电池术语、项目与关联知识 | 开放入口 |

## 数据标准、本体与电池护照

| 名称 | 链接 | 格式/技术 | 用途 | 开放性 |
| --- | --- | --- | --- | --- |
| Battery Data Format (BDF) | [GitHub](https://github.com/battery-data-alliance/battery-data-format) | Parquet/Python | 电池实验数据统一结构与转换 | 开源 |
| BPX — Battery Parameter eXchange | [Standard](https://bpxstandard.com/) · [GitHub](https://github.com/FaradayInstitution/BPX) | JSON Schema | DFN/SPM 参数、方程和验证数据交换 | 开放标准 |
| BattINFO | [GitHub](https://github.com/BIG-MAP/BattINFO) | OWL/RDF/JSON-LD/Python | 电芯、材料、测试、数据集语义与验证 | Apache-2.0 |
| EMMO domain-battery | [GitHub](https://github.com/emmo-repo/domain-battery) | OWL/RDF | 电池领域本体 | CC-BY-4.0 |
| EMMO domain-electrochemistry | [GitHub](https://github.com/emmo-repo/domain-electrochemistry) | OWL/RDF | 电化学系统、材料、方法和数据本体 | CC-BY-4.0 |
| Battery Pass Data Model | [GitHub](https://github.com/batterypass/BatteryPassDataModel) | RDF/JSON-LD/JSON Schema/OpenAPI/AAS | 欧盟电池护照字段和交换模型 | CC-BY-4.0；核对版本 |
| Battery Pass Content Guidance | [Project](https://thebatterypass.eu/resources/) | PDF/指南 | 护照字段、可持续性和供应链要求 | 开放资料 |
| Frictionless Data | [Specs](https://specs.frictionlessdata.io/) | JSON/CSV | 数据包、表格 schema 与校验 | 开放标准；通用 |
| RO-Crate | [Specification](https://www.researchobject.org/ro-crate/) | JSON-LD | 数据、代码、论文与来源关系打包 | 开放标准；通用 |

## 制造、成本、回收与生命周期

| 名称 | 链接 | 类型 | 用途 | 访问说明 |
| --- | --- | --- | --- | --- |
| BatPaC | [Argonne](https://www.anl.gov/partnerships/batpac-battery-manufacturing-cost-estimation) | Excel 模型 | 电芯/电池包设计和制造成本 | 免费下载/依许可 |
| EverBatt Lite | [Argonne](https://everbatt.amd.anl.gov/) | Web 模型 | 闭环回收的成本、能源与排放 | 免费 Web；功能为 EverBatt 子集 |
| GREET | [Argonne](https://greet.anl.gov/) | 生命周期模型 | 材料、车辆、燃料与电池生命周期分析 | 免费注册/依许可 |
| ReCell Center | [Portal](https://recellcenter.org/) | 研究集合 | 锂电池直接回收、过程与模型 | 开放资料/数据分散 |
| NREL BLAST-Lite | [GitHub](https://github.com/NREL/BLAST-Lite) | Python | 不同应用工况下的退化与寿命 | 开源 |
| openLCA | [Project](https://www.openlca.org/) | Java/GUI | 生命周期评价建模 | 软件开放；数据库许可各异 |
| Brightway | [GitHub](https://github.com/brightway-lca/brightway2) | Python | 可编程 LCA 与情景分析 | BSD；数据库另行授权 |
| ecoinvent | [Database](https://ecoinvent.org/) | LCI 数据库 | 电池材料、能源、运输和回收背景数据 | 商业/学术许可 |
| GREET Python Interface | [GitHub search](https://github.com/search?q=GREET+lifecycle&type=repositories) | Python/第三方 | GREET 自动化与结果处理的社区实现 | 非官方，逐项核验 |
| Argonne CAMP Facility | [Portal](https://www.anl.gov/cse/cell-analysis-modeling-and-prototyping-camp-facility) | 制造与表征资源 | 标准电极、电芯制造和公开研究入口 | 项目资料 |

## 测试标准与法规入口

标准正文经常需要购买；下表链接到发布机构或法规原文，不提供未经授权的副本。

| 标准/法规 | 官方入口 | 范围 | 访问 |
| --- | --- | --- | --- |
| UN Manual of Tests and Criteria, 38.3 | [UNECE](https://unece.org/transport/dangerous-goods/manual-tests-and-criteria) | 锂电池运输 T.1–T.8 | 官方 PDF 通常开放 |
| IATA Lithium Battery Guidance | [IATA](https://www.iata.org/en/programs/cargo/dgr/lithium-batteries/) | 航空运输、包装和申报 | 指南开放/规则混合 |
| IEC 62133-2 | [IEC](https://webstore.iec.ch/en/publication/32662) | 便携式密封锂电芯/电池安全 | 标准付费 |
| IEC 62619 | [IEC](https://webstore.iec.ch/en/publication/64073) | 工业二次锂电芯/电池安全 | 标准付费 |
| IEC 62660 series | [IEC search](https://webstore.iec.ch/searchform&q=IEC%2062660) | 电动道路车辆锂离子电芯性能、可靠性和安全 | 标准付费 |
| UL 1642 | [UL Standards](https://www.shopulstandards.com/ProductDetail.aspx?productId=UL1642) | 锂电芯安全 | 标准付费 |
| UL 1973 | [UL Standards](https://www.shopulstandards.com/ProductDetail.aspx?productId=UL1973) | 固定式/车辆辅助电池 | 标准付费 |
| UL 2580 | [UL Standards](https://www.shopulstandards.com/ProductDetail.aspx?productId=UL2580) | 电动车电池 | 标准付费 |
| UL 9540A | [UL Solutions](https://www.ul.com/services/ul-9540a-test-method) | 储能系统热失控传播测试方法 | 介绍开放/标准依授权 |
| SAE J2464 | [SAE](https://www.sae.org/standards/content/j2464_202111/) | 电动车储能系统滥用测试 | 标准付费 |
| ISO 12405 series | [ISO search](https://www.iso.org/search.html?q=ISO%2012405) | 电动道路车辆锂离子电池包/系统测试 | 标准付费 |
| EU Battery Regulation 2023/1542 | [EUR-Lex](https://eur-lex.europa.eu/eli/reg/2023/1542/oj) | 可持续性、安全、标签、护照与回收 | 法规原文开放 |
| 中国国家标准全文公开系统 | [SAMR](https://openstd.samr.gov.cn/) | GB/GB/T 电池标准检索 | 部分全文开放 |
## 致谢

- [pauljgasper/awesome-battery-data](https://github.com/pauljgasper/awesome-battery-data)：本目录的主要结构参考与首批资源线索。
- 各开源项目维护者、数据作者、标准机构和公共研究资助机构。
