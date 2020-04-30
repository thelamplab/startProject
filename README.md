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

### General directory structure:
1. analysis: This directory should contain the analysis code, divided into subdirectories (typically `python`, `ipynb`, and `prototype`, the latter being for fMRI analysis)
2. data: This should contain all datafiles
3. experiment: This should contain all of the code required to run the experiment
4. ethics: This should contain all documents relevant to REB approvals
5. figures: This is where you should save any figures, preferably in PDF format, that are output by your analysis code
6. paper: This should contain the writeup for the paper based on these data
7. presentations: This should contain any slides or posters for presentations given based on these data
8. scratch: This is the wild west space where you can workshop code. Its usually a good idea for this to have parallel depth to the actual code (i.e. `scratch/python`) so that any relative paths still function
9. stimuli: This is where you place any stimuli (e.g. word lists, images, sounds, videos, training images for deep nets)
10. updates: This should contain a running document that details notes on the evolution of the project
11. utils: Loose ends, this should contain both an environment.yml file for any relevant conda environments, and a txt file with the commands required to build it (in casy yml fails, which it often does)
