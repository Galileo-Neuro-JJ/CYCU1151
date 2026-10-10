# CYCU1151

## Requirements
1. Python 3.8.3

2. All packages can be installed using the following command:
> pip install -r requirements.txt

## Applying analyses to other datasets (Written by James B Isbister, james.isbister@epfl.ch)
The code is designed to analyse the dataset used in the study and has not been tested for other datasets. Those wishing to apply the analyses to alternative datasets, however, must organise their data in the form that the in vivo data is given here. Particularly, data should be organised with the following directory structure (see dataset).


```
InVivoData 
│
└───Session1
│   │   UNIT_LAYERS.txt # List of length N, where N is the number of neurons for the experimental session.
│   │   UNIT_EXC_INH_CHARACTERISATIONS.txt
│   │	UNIT_BARRELS.txt
│   │
│   └───CutOutSpikes
│   │   │
│	│	└───Spikes_-50-150
│   │   │	│	Unit1.txt
│   │   │	│	Unit2.txt
│   │   │	│	Unit3.txt	
│   │   │	│	...
│   │   │	│
│   └───ConditionInformation
│   │   │	stimulation_frequency_for_each_condition.txt
│   │   │	stimulated_whisker_for_each_condition.txt
│   │   │	start_indices_for_each_condition_in_sorted_trial_arrays.txt	
│   │   │	number_of_trials_containing_mandatory_codes_for_each_sorted_condition.txt
│
└───Sesssion2
│   │ ...	
```

Within each experimental session directory (i.e. Session1), data is organised for N neurons and C Conditions, where each condition has a total of T<sub>c<sub> trials. For each experimental session, the data files must contain the following data:
- **"start_indices_for_each_condition_in_sorted_trial_arrays.txt"**	must specificy the first trial index of each condition (giving a list of length C).
- **"number_of_trials_containing_mandatory_codes_for_each_sorted_condition.txt"**	must specificy the number of trials T<sub>c<sub> for each condition (giving a list of length C).
- Each **"UnitX.txt"** file should contain the spike times of the particular neuron X, where each line corresponds to the spike times on a single trial. Spikes times on a single trial should be tab delineated.

The variable named "original_spike_cut" on line X of **"recipes/investigation_recipe.json"** must specificy the range of the time window (around stimulus onset) that spikes are drawn from. A time window of [-50, 150] is recommended. 

The variables "experiment_codes" and "experiment_handles" must also be updated on lines X of **"recipes/investigation_recipe.json"** to match the experimental codes and data subdirectories (see provided in vivo data).

The remaining files contain information that is specific to the dataset. Particularly, analysis which used neuron layer, E/I, barrel, stimulation frequency and stimulated whisker information is specific to this study. Currently, such files must be generated as placeholders, as follows:
- UNIT_LAYERS.txt - A list of length N with integer values between 2 and 6.
- UNIT_EXC_INH_CHARACTERISATIONS.txt - a list of length N with values EXC and/or INH
- UNIT_BARRELS.txt - a list of length N with values such as C0, D1, D2, D3
- stimulation_frequency_for_each_condition.txt - a list of length C with values specifying the stimulation frequency (i.e. 1, 2)
- stimulated_whisker_for_each_condition.txt - a list of length C with values such as C0, D1, D2, D3

## Contact
If you have any questions or wish to contribute, please contact: 
- Jyh-Jang Sun (jjsun@cycu.edu.tw)
