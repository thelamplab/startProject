# startProject

This repo is to make it easy to initialize a new project with a familiar directory structure. Anywhere you see `$NEW`, replace this with what your new project is called. In general this name should have no spaces, shouldn't be longer than the title of this repo (~12 characters), and should be thematically related to the project.

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

This is simply a set of directories to facilitate the sharing of code and information, as well as revisiting projects years from now when the intial creators might not be so easy to track down. The more uniform this is, the easier it will be to handle projects in the lab long-terms. The idea is that on personal and lab computers, as well as the cluster, all of these directories exist for every project, and are mirrored on github. Depending on the need, various subdirectories can be parcelled out for each purpose (e.g. experiment code, and stimuli to online host for web experiments; prep code or analysis to cluster).

In general, large files (i.e. anything but small text or csv files and very small sets of images) should be kept off of github, but retained in your local repo, and in lab backups. Data should **never** be posted to github though (it can stay local).

In the event that you run multiple experiments in the same project, simply number the `analysis` ipynb notebooks and comment any python code with the experiment its relevant to. Better yet, you can write code amenable to data from multiple experiments by changing an argument. Data from each experiment should be placed in its own `E2`, `E3`, etc subdirectory. Experiment code can similarly be in its own `E2`, `E3` subdirectory. Stimuli, if different, can be placed in their own `E2`, `E3` subdirectory.  Add a new OneSheet describing the new experiment in `updates`. If there are stimuli that are necessary for prep, or generic across experiments, they can be placed in their own clearly named subdirectories within `stimuli`.

Bear in mind that at all steps, the goal is to make this easy to use for someone that's not in the lab. Don't be shy about including new `README.md` files in directories to provide a roadmap for its use, or to explain the steps required to set up the environment to run experimental code.


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

### Datafile naming convention:

All data that you write out should be named as follows, where $1 through $4 are filled in depending on the experiment, subject, phase, and extension.

$1-$2_$3.$4

$1 -- name of new project ( <= 12 chars, no spaces )

$2 -- participant number (start at 1001 for first participant in E1, 4103 is 103rd participant in E4)

$3 -- descriptive label for what this is (in memory task data could be 'Enc' for encoding, in fMRI, 'func01' for first functional run)

$4 -- extension ( depends on the type of data, e.g. csv beh data )

### Incorporated in all data:

All datafiles written should contain the project name, participant number, date and time for each entry

Even if you don't think you're interested in something, its usually not a bad idea to collect it.
