# CloudcomparePlugins

There are many issues while trying to build CloudCompare wheels and I hope these pre-build wheels with a simple tutorial will help.

## Notes
This method is tested using Ubuntu in a Linux subsystem in Windows.

## Wheels

[`Wheels`](./Wheels/): Images used in this repository

## Installation
1. First you need to install brew in your ubuntu
   
 ```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
 ```
for more info visit https://docs.brew.sh/Homebrew-on-Linux

2. Install qt

```bash
brew install qt
 ```
for more info visit https://formulae.brew.sh/formula/qt

2.5 In case of qt failing to install because of the soft limit : 
If we increase the soft limit and run our program again, we should see it open more files. We'll use the ulimit command and the -n (open files) option with a numeric value of 2048. This will be the new soft limit.

```bash
ulimit -n 2048
 ```
3. Usually an error about libQT is present, to fix it use in your ubuntu command prompt :
```bash
sudo apt-get install libqt5opengl5
 ```
```bash
sudo apt-get install libqt5concurrent5
 ```
3.5 Other method of fix for the libQt
```bash
sudo strip --remove-section=.note.ABI-tag /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
 ```

4. Create an environemnt wich conda 3.9.6 (other env might work too, but this version is tested)
```bash
conda create --name your_env python=3.9.6
```

5. Activate the new env :
```bash
conda activate your_env
```
5. Install the wheels available in this repository :
```bash
pip install pycc-0.0.1-cp39-cp39-linux_x86_64.whl
```
```bash
pip install cccorelib-0.0.1-cp39-cp39-linux_x86_64.whl
```


## Acknowledgements
The original repository where you can build the wheels from scratch :

https://github.com/tmontaigu/CloudCompare-PythonRuntime/blob/master/docs/building.rst#building-as-independent-wheels
