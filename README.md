# ISIS-on-Windows-11
This is the workflow I used to install ISIS on my PC, I slightly modified Trent Hare's workflow and maybe it could be useful to someone (https://planetarygis.blogspot.com/2017/07/isis3-on-windows-10-bash.html)

# Get Linux for Windows 11 using the Windows App Store (Ubuntu 22)
Open Windows Power Shell and type:
```
wsl –-update
```

# Run Ubuntu and update it typing:
```
sudo apt-get update
sudo apt-get upgrade
```

# Get Anaconda:
```
wget (the url of a version of the software (https://repo.anaconda.com/archive/))
```
```
bash (the name of the file you downloaded)
```
if the installation does not work download another version of anaconda and try again!

# Get ISIS
```
conda create -n asp3
conda activate asp3
conda config --env --add channels conda-forge
conda config --env --add channels usgs-astrogeology
conda config --env --add channels nasa-ames-stereo-pipeline
conda install  -c nasa-ames-stereo-pipeline -c usgs-astrogeology -c conda-forge stereo-pipeline==3.3.0
```
```
python $CONDA_PREFIX/scripts/isisVarInit.py
```
BUT using the the following optional command line you can specify a directory:
```
python $CONDA_PREFIX/scripts/isisVarInit.py --data-dir=[path to data directory]
```
to download all ISIS data:
```
downloadIsisData all $ISISDATA
```
To move to a specific directory, for example an external hard disk you can write: 
```
cd /mnt/d/…/
```

# If the actualization of cube kernels gives you problems and an error message such as: 
PROGRAMMER ERROR No value or default value to translate for translation group [MissionName] 
You can use the server typing something similar to:
```
spiceinit from=name_file web=yes url=https://astrogeology.usgs.gov/apis/ale/v0.9.1/spiceserver/
```
