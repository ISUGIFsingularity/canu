# Singularity container recipe and run script for the MaSuRCA assembler

### Clone this repository

```
mkdir isugif
cd isugif
git clone git@github.com:ISUGIFsingularity/canu.git
```

### Place singularity container into SIMG folder inside this repo

You can pull the singularity image using these commands

```
cd canu
mkdir SIMG
cd SIMG
singularity pull shub://ISUGIFsingularity/canu:1.8.0
ln -s ISUGIFsingularity-canu-master-1.8.0.simg  ISUGIFsingularity-canu-master.simg
```

### Add Alias and PATH

Place the following into your .bashrc folder for container use

```
#make sure you are in the canu folder that corresponds to the Path2thisRepo
export canugit=`pwd`
export PATH=$PATH:$canugit/wrappers
```

Place the following into your .bashrc folder to use scripts without container (preferred method unless testing container functions)

```
export canugit=`pwd`
export PATH=$PATH:$canugit/canu
```


### Notes

For this to function properly had to add ```--bind $canugit:/mnt``` to the wrappers

Example

```
 singularity exec --bind $canugit:/mnt --bind $PWD $canugit/SIMG/ISUGIFsingularity-canu-master.simg /mnt/canu/summary.sh
```
