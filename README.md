# startProject

This repo is to make it easy to initialize a new project with a familiar directory structure. Anywhere you see `$NEW`, replace this with what your new project is called.

1. This first block of code provides the ingredients for you to be able to duplicate the directory structure, but as a new repository.

```bash
git clone --bare https://github.com/thelamplab/startProject.git
cd startProject.git
```
2. **BEFORE** moving on, make new repo on GitHub.com under thelamplab organization entitled `$NEW`. **DO NOT** initialize with README.

3. This next command establishes your new project repo remotely (i.e. on github.com). Remember to **replace** `$NEW` with what your new project is called.

```bash
git push --mirror https://github.com/thelamplab/$NEW.git
```

4. This next set of commands cleans up the leftover ingredients, and brings your new project onto your local machine.

```bash
cd ..
rm -rf startProject.git
git clone https://github.com/thelamplab/$NEW.git
```

## Structure

This is simply a set of directories to facilitate the longevity of the data. The more uniform this is, the easier it will be to handle projects in the lab long-term, including passing projects between researchers. The idea is that on the lab computers, and cluster, all of these directories exist for every project, and are mirrored on github. Depending on the need, various subdirectories can be parcelled out. 

In general, large files (i.e. anything but small text or csv files and very small sets of images) should be kept off of github, but retained in your local repo. Data should **NOT** be posted to github though (it can stay local).

In the event that you run multiple experiments in the same project, simply number `analysis` notebooks and comment any python code with the experiment its relevant to. Better yet, make shared functions amenable to data from multiple experiments with an argument. Data should be placed in its own new `E2`, `E3`, etc subdirectory. Experiment code can similarly be in its own `E2`, `E3` subdirectory. Stimuli, if different, can be placed in their own `E2`, `E3` subdirectory. Add a new OneSheet describing the new experiment in `updates`.


### Directories and what they're for:

| Directory     | What it's for             |
| ------------- |-------------    |
| analysis | analysis code, divided into subdirectories (typically `python`, `ipynb`, and `prototype`, the latter being for fMRI analysis strucutre, similar in spirit to [neuropipe](https://github.com/ntblab/neuropipe)) |
| data | all datafiles, divided by experiment (e.g. `E1`) |
|experiment | all of the code required to run the experiment, divided by experiment (e.g. `E1`) |
|ethics | all documents relevant to REB approvals | 
|figures | figures, preferably in `.pdf` format, that are output by your analysis code | 
|paper | the manuscript based on these data, typically `.tex` format for overleaf | 
|presentations | any slides or posters for presentations given based on these data | 
|scratch | the wild west space where you can workshop code. Its usually a good idea for this to have parallel depth to the actual code (i.e. `scratch/python`) so that any relative paths still function | 
|stimuli | any stimuli needed for prep or experiment (e.g. word lists, images, sounds, videos, training images for deep nets), divided by experiment (e.g. `E1`)|
|updates | the oneSheet description for each study, a running document that details notes on the evolution of the project|
|utils | an environment.yml file for any relevant conda environments, and a txt file with the commands required to build it (in casy yml fails, which it often does), other odds and ends (e.g. network architectures, weights, supporting text files)|
