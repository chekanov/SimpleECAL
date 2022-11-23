# SimpleECAL 

This is an example of CLIC-like barrel ECAL with crystals (PbWO4). It uses the original CLIC geometry files and variables.
The only difference is that it uses 1 cm cell sizes (to speed up calculations).

The geometry is implemented in 

```bash
compact/ECalBarrel_DualCrystal.xml
```

Check the ECAL geometry using this top-level file SimpleECAL.xml that includes "ECalBarrel_DualCrystal.xml":

```bash
geoDisplay SimpleECAL.xml
```

Run this example using the script "A_RUN". It  makes the ROOT file (usieng Sarah's example). This program works when using material "PbWO4". This does not give scintillation photons, but you will see Cherenkov photons.

If you will replace PbWO4 with E_PbWO4 inside "ECalBarrel_DualCrystal.xml", both Cherenkov and scintillation photons will be printed, 
but the program will be running forever (kill it from another window!). 
 

This program is based on the SingleDualCrystal and the CLIC geometry files.

##  Installation 

```bash
source /cvmfs/sft.cern.ch/lcg/views/LCG_101/x86_64-centos7-gcc11-opt/setup.sh
git clone https://github.com/AIDASoft/DD4hep.git
cd DD4hep/examples
git clone git@github.com:chekanov/SimpleECAL.git 
# edit CMakeLists.txt and add SimpleECAL to
# SET(DD4HEP _EXAMPLES "AlignDet CLICSiD ClientTests Conditions DDCMS DDCodex DDDigi DDG4 DDG4_MySensDet LHeD Optica\
lSurfaces Persistency DDCAD SimpleDetector SimpleECAL"
CACHE STRING "List of DD4hep Examples to build")

cd ..
mkdir build
mkdir install
cd build/
cmake -DDD4HEP_USE_GEANT4=ON -DBoost_NO_BOOST_CMAKE=ON -DDD4HEP_USE_LCIO=ON -DBUILD_TESTING=ON -DROOT_DIR=$ROOTSYS -D CMAKE_BUILD_TYPE=Release -DDD4HEP_BUILD_EXAMPLES=ON ..
make -j4
make install
cd ..
source bin/thisdd4hep.sh
```

