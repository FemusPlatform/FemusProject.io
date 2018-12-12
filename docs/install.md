===========================================================================
Scripts:
============================================================================
platform  (NumericalPlatform)   

/dsk5/dsk5/platform
├── init_platform.sh
├── PLAT_BUILD
│   ├── gui_dowload.sh
│   ├── gui_guide.sh
│   ├── gui_install_package.sh
│   ├── install_scripts
│   │   ├── code_versions.sh
│   │   ├── fblaslapack.sh
│   │   ├── femus.sh
│   │   ├── foam_repo.sh
│   │   ├── libmesh.sh
│   │   ├── medCoupling.sh
│   │   ├── med.sh
│   │   ├── openmpi.sh
│   │   ├── petsc_dbg.sh
│   │   ├── petsc_opt.sh
│   │   ├── plat_conf_template.sh
│   │   ├── platform.sh
│   │   ├── requirements.sh
│   │   ├── salome.sh
│   │   └── utility.sh
│   ├── install.sh
│   ├── package_logs
│   ├── packages_targz
│   └── plat_requirements.log
├── PLAT_CODES
├── plat_conf.sh
├── PLAT_THIRD_PARTY
├── PLAT_USERS
├── PLAT_VISU
├── README.md
└── readme.txt    
                      
                      
===================================================================
GUI
Download       "Dowload packages" \
SetUpPlatform  "Set up Numerical Platform structure" \
InstThirdParty "Install Third Party Packages" \
InstCodes      "Install Numerical Codes" \
Guide          "Installation guide " \
Editor         "Start a text editor" \
Exit           "Exit to the shell" 2>"${INPUT}"
===================================================================


=================================================
shell commands
=================================================
1) in dir =../platform/  
$>source  init_platform.sh     
2) GUI     SetUpPlatform -> PLAT_BUILD/install_scripts/platform.sh                  
3) GUI     InstThirdParty-> gui_install_package.sh                               
4) GUI     InstCodes-> gui_install_package.sh                        
                      
                      
                      
=================================================                      
------------------------------------------------
1A) init_platform.sh
------------------------------------------------
=================================================
cd PLAT_BUILD
1A1> source install.sh 


------------------------------------------------
1B) PLAT_BUILD/install.sh
------------------------------------------------
1B1> source gui_dowload.sh -> function show_dowloading()
1B2> source gui_guide.sh   -> function show_guide(){
1B3> source gui_install_package.sh -> source install_scripts/code_versions.sh
                                  function show_platform()
                                  function show_third_packages()
1B4> source install_scripts/requirements.sh
 
 
 
 ------------------------------------------------
1B3) PLAT_BUILD/install_scripts/code_versions.sh
------------------------------------------------ 
export DefaultLatest="latest"
# SALOME
export SalomeLast="8.4.0" export SalomeLastest="8.5.0"
# OPENMPI
export OpenmpiLast="3.1.3"
# PETSC
export PetscLast='3.10.2' export PetscLatest=$DefaultLatest
# LIBMESH
export LibmeshLast='1.3.1' export LibmeshLatest=$DefaultLatest
 
 ------------------------------------------------
1B4) PLAT_BUILD/install_scripts/requirements.sh
------------------------------------------------
function  command_exists (){...}
function check_executable (){...}
 
echo "Check linux distribution " 
echo "Check linux distribution " >> requirements.log
cat /etc/*-release
cat /etc/*-release >> requirements.log

check_executable dialog
check_executable gcc
check_executable g++ 

echo
 
 
 =================================================                      
------------------------------------------------
2A) PLAT_BUILD/install_scripts/platform.sh
------------------------------------------------
=================================================
creation 1 Level


 
echo $SCRIPT_NAME ": 1c Platform set up 1 Level directory  ------> plat_conf.sh: summary "
echo "-----------------------------------------------------------------------------------------"
echo $SCRIPT_NAME ": 1c Platform DIR (platform or software or ...) is = " $PLAT_DIR
echo
echo $SCRIPT_NAME ": 1c BUILD dir (BUILD_DIR) is                      = " $BUILD_DIR
echo $SCRIPT_NAME ": 1c INSTALL_BUILD_TAR_DIR (package archive dir)   = " $INSTALL_BUILD_TAR_DIR
echo $SCRIPT_NAME ": 1c INSTALL_PLAT_LOG_DIR  (log dir)               = " $INSTALL_PLAT_LOG_DIR
echo
echo $SCRIPT_NAME ": 1c PLAT_THIRD_PARTY_DIR  (third party code dir)  = " $PLAT_THIRD_PARTY_DIR
echo $SCRIPT_NAME ": 1c PLAT_USERS_DIR  (users dir)                   = " $PLAT_USERS_DIR
echo $SCRIPT_NAME ": 1c PLAT_CODES_DIR  (codes dir)                   = " $PLAT_CODES_DIR
echo $SCRIPT_NAME ": 1c PLAT_VISU  (visualization dir)                = " $PLAT_VISU_DIR
echo "-----------------------------------------------------------------------------------------"
 
export PLAT_DIR=....path/platform
change ....path -> real environment
sed -e "4s|.*|export PLAT_DIR=$PLAT_DIR|" $PLAT_DIR/PLAT_BUILD/install_scripts/plat_conf_template.sh>$PLAT_DIR/plat_conf.sh

-> plat_conf.sh  



=================================================                      
------------------------------------------------
3A InstThirdParty
------------------------------------------------
=================================================

3A1) Salome (8.4)

/dsk5/dsk5/platform
├── init_platform.sh
├── PLAT_BUILD
│   ├── packages_targz
│   │   └── Salome-V8.4.0-univ_public.run
│   └── Salome-V8_4_0-univ
│       ├── create_appli.sh
│       ├── desktop-file-install-desktop.log
│       ├── desktop-file-install-menu.log
│       ├── icon.png
│       ├── modules
│       ├── plugins
│       ├── prerequisites
│       ├── README
│       ├── salome_context.cfg
│       ├── salome_modules.sh
│       ├── salome_post_install.py
│       ├── salome_prerequisites.sh
│       ├── Salome_V8_4_0.desktop
│       ├── sha1_collections.txt
│       └── tools
├── PLAT_CODES
├── plat_conf.sh
├── PLAT_THIRD_PARTY
│   ├── hdf5 -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/salome/prerequisites/Hdf5-1814/
│   ├── MED_mod -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/salome/modules/MED_V8_4_0/
│   └── salome -> /dsk5/dsk5/platform/PLAT_BUILD/Salome-V8_4_0-univ
├── PLAT_USERS
├── PLAT_VISU
│   └── appli_salome
│       ├── appli_V8_4_0.log
│       ├── bin
│       ├── config_appli.xml
│       ├── envd -> /dsk5/dsk5/platform/PLAT_VISU/appli_salome/bin/salome/appliskel/envd
│       ├── env.d
│       ├── getAppliPath.py -> /dsk5/dsk5/platform/PLAT_VISU/appli_salome/bin/salome/appliskel/getAppliPath.py
│       ├── idl
│       ├── kill_remote_containers.py -> /dsk5/dsk5/platform/PLAT_VISU/appli_salome/bin/salome/appliskel/kill_remote_containers.py
│       ├── lib
│       ├── runRemote.sh -> /dsk5/dsk5/platform/PLAT_VISU/appli_salome/bin/salome/appliskel/runRemote.sh
│       ├── salome
│       ├── SalomeApp.xml
│       ├── sha1_collections.txt
│       ├── share
│       ├── update_catalogs.py -> /dsk5/dsk5/platform/PLAT_VISU/appli_salome/bin/salome/appliskel/update_catalogs.py
│       └── USERS
├── README.md
└── readme.txt


3A1) Openmpi (3.1.3)


/dsk5/dsk5/platform
├── init_platform.sh
├── PLAT_BUILD
│   ├── gui_dowload.sh
│   ├── gui_guide.sh
│   ├── gui_install_package.sh
│   ├── install_scripts
│   ├── install.sh
│   ├── openmpi-3.1.3
│   │   ├── aclocal.m4
│   │   ├── AUTHORS
│   │   ├── autogen.pl
│   │   ├── config
│   │   ├── config.log
│   │   ├── config.lt
│   │   ├── config.status
│   │   ├── configure
│   │   ├── configure.ac
│   │   ├── contrib
│   │   ├── Doxyfile
│   │   ├── examples
│   │   ├── INSTALL
│   │   ├── libtool
│   │   ├── LICENSE
│   │   ├── Makefile
│   │   ├── Makefile.am
│   │   ├── Makefile.in
│   │   ├── Makefile.ompi-rules
│   │   ├── NEWS
│   │   ├── ompi
│   │   ├── opal
│   │   ├── orte
│   │   ├── oshmem
│   │   ├── README
│   │   ├── README.JAVA.txt
│   │   ├── test
│   │   └── VERSION
│   ├── package_logs
│   │   ├── openmpi_compile.log
│   │   ├── openmpi_config.log
│   │   ├── openmpi_install.log
│   │   └── plat_requirements.log
│   ├── packages_targz
│   │   ├── openmpi-3.1.3.tar.gz
│   │   └── Salome-V8.4.0-univ_public.run
│   ├── plat_requirements.log
│   └── Salome-V8_4_0-univ
├── PLAT_CODES
├── plat_conf.sh
├── PLAT_THIRD_PARTY
│   ├── hdf5 -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/salome/prerequisites/Hdf5-1814/
│   ├── openmpi -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/openmpi-3.1.3
│   ├── openmpi-3.1.3
│   │   ├── bin
│   │   ├── etc
│   │   ├── include
│   │   ├── lib -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/openmpi/lib64
│   │   ├── lib64
│   │   └── share
│   └── salome -> /dsk5/dsk5/platform/PLAT_BUILD/Salome-V8_4_0-univ
├── PLAT_USERS
├── PLAT_VISU
├── README.md
└── readme.txt

84 directories, 117 files


3A2) med

/dsk5/dsk5/platform
├── init_platform.sh
├── PLAT_BUILD
│   ├── gui_dowload.sh
│   ├── gui_guide.sh
│   ├── gui_install_package.sh
│   ├── install_scripts
│   │   ├── code_versions.sh
│   │   ├── fblaslapack.sh
│   │   ├── femus.sh
│   │   ├── foam_repo.sh
│   │   ├── libmesh.sh
│   │   ├── medCoupling.sh
│   │   ├── med.sh
│   │   ├── openmpi.sh
│   │   ├── petsc_dbg.sh
│   │   ├── petsc_opt.sh
│   │   ├── plat_conf_template.sh
│   │   ├── platform.sh
│   │   ├── requirements.sh
│   │   ├── salome.sh
│   │   └── utility.sh
│   ├── install.sh
│   ├── med-3.3.1
│   │   ├── CMakeCache.txt
│   │   ├── CMakeFiles
│   │   ├── cmake_install.cmake
│   │   ├── CTestTestfile.cmake
│   │   ├── include
│   │   ├── install_manifest.txt
│   │   ├── Makefile
│   │   ├── med-3.3.1
│   │   ├── MEDFileConfig.cmake
│   │   ├── MEDFileConfigVersion.cmake
│   │   ├── MEDFileTargets.cmake
│   │   ├── src
│   │   ├── testFortranIntegerSize1.f90
│   │   ├── testFortranIntegerSize2.f90
│   │   ├── testFortranIntegerSize4.f90
│   │   ├── tests
│   │   ├── testTimeSysTime.c
│   │   ├── to_install
│   │   ├── tools
│   │   ├── xmdump2
│   │   └── xmdump3
│   ├── package_logs
│   │   ├── med_compile.log
│   │   └── med_install.log
│   ├── packages_targz
│   ├── plat_requirements.log
│   └── Salome-V8_4_0-univ
├── PLAT_CODES
├── plat_conf.sh
├── PLAT_THIRD_PARTY
│   ├── hdf5 -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/salome/prerequisites/Hdf5-1814/
│   ├── med -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/med-3.3.1
│   ├── med-3.3.1
│   │   ├── bin
│   │   ├── include
│   │   ├── lib
│   │   ├── lib64 -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/med-3.3.1/lib
│   │   └── share
│   ├── MED_mod -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/salome/modules/MED_V8_4_0/
│   ├── openmpi -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/openmpi-3.1.3
│   ├── openmpi-3.1.3
│   └── salome -> /dsk5/dsk5/platform/PLAT_BUILD/Salome-V8_4_0-univ
├── PLAT_USERS
├── PLAT_VISU
│   └── appli_salome
├── README.md
└── readme.txt

84 directories, 117 files


3A3) medCoupling

/dsk5/dsk5/platform
├── init_platform.sh
├── PLAT_BUILD
│   ├── MedCoupling-8.4.0
│   │   ├── adm_local
│   │   ├── CMakeCache.txt
│   │   ├── CMakeFiles
│   │   ├── cmake_install.cmake
│   │   ├── CTestTestfile.cmake
│   │   ├── install_manifest.txt
│   │   ├── Makefile
│   │   ├── MedCoupling-8.4.0
│   │   ├── MEDCouplingConfigVersion.cmake
│   │   ├── MEDCouplingTargets.cmake
│   │   ├── MEDCoupling_version.h
│   │   ├── resources
│   │   ├── src
│   │   └── to_install
│   ├── package_logs
│   │   ├── medCoupling_compile.log
│   │   └── medCoupling_install.log
│   ├── packages_targz
│   ├── plat_requirements.log
├── PLAT_CODES
├── plat_conf.sh
├── PLAT_THIRD_PARTY
│   ├── hdf5 -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/salome/prerequisites/Hdf5-1814/
│   ├── med -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/med-3.3.1
│   ├── med-3.3.1
│   ├── MED_coupling -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/MedCoupling-8.4.0
│   ├── MedCoupling-8.4.0
│   │   ├── adm_local
│   │   ├── bin
│   │   ├── cmake_files
│   │   ├── include
│   │   ├── lib
│   │   ├── lib64 -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/MedCoupling-8.4.0/lib
│   │   ├── share
│   │   └── tests
│   ├── MED_mod -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/salome/modules/MED_V8_4_0/
│   └── salome -> /dsk5/dsk5/platform/PLAT_BUILD/Salome-V8_4_0-univ
├── PLAT_USERS
├── PLAT_VISU
│   └── appli_salome
├── README.md
└── readme.txt


3A4) petsc_dbg (3.10.2)

/dsk5/dsk5/platform
├── init_platform.sh
├── PLAT_BUILD
│   ├── gui_dowload.sh
│   ├── gui_guide.sh
│   ├── gui_install_package.sh
│   ├── install_scripts
│   ├── install.sh
│   ├── med-3.3.1
│   ├── MedCoupling-8.4.0
│   ├── openmpi-3.1.3
│   ├── package_logs
│   │   ├── petsc-dbg_compiling.log
│   │   ├── petsc-dbg_config.log
│   │   ├── petsc-dbg_install.log
│   │   ├── petsc-dbg_testing.log
│   │   ├── petsc-opt_compiling.log
│   │   ├── petsc-opt_config.log
│   │   └── plat_requirements.log
│   ├── packages_targz
│   ├── petsc-3.10.2
│   │   ├── buildsystem.log
│   │   ├── CMakeLists.txt
│   │   ├── config
│   │   ├── configure
│   │   ├── configure.log -> linux-opt/lib/petsc/conf/configure.log
│   │   ├── configure.log.bkp -> linux-dbg/lib/petsc/conf/configure.log
│   │   ├── CONTRIBUTING
│   │   ├── CTAGS
│   │   ├── docs
│   │   ├── gmakefile
│   │   ├── gmakefile.test
│   │   ├── include
│   │   ├── index.html
│   │   ├── interfaces
│   │   ├── Jenkinsfile
│   │   ├── lib
│   │   ├── LICENSE
│   │   ├── linux-dbg
│   │   ├── linux-opt
│   │   ├── makefile
│   │   ├── makefile.html
│   │   ├── make.log -> linux-opt/lib/petsc/conf/make.log
│   │   ├── RDict.log
│   │   ├── setup.py
│   │   ├── share
│   │   ├── src
│   │   ├── systems
│   │   └── TAGS
│   ├── plat_requirements.log
│   └── Salome-V8_4_0-univ
├── PLAT_CODES
├── plat_conf.sh
├── PLAT_THIRD_PARTY
│   ├── hdf5 -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/salome/prerequisites/Hdf5-1814/
│   ├── med -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/med-3.3.1
│   ├── med-3.3.1
│   ├── MED_coupling -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/MedCoupling-8.4.0
│   ├── MedCoupling-8.4.0
│   ├── MED_mod -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/salome/modules/MED_V8_4_0/
│   ├── openmpi -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/openmpi-3.1.3
│   ├── openmpi-3.1.3
│   ├── petsc-3.10.2
│   │   ├── linux-dbg
│   │   └── linux-opt
│   └── salome -> /dsk5/dsk5/platform/PLAT_BUILD/Salome-V8_4_0-univ
├── PLAT_USERS
├── PLAT_VISU
├── README.md
└── readme.txt



====================================
Complete install third-party soft
====================================
/dsk5/dsk5/platform
├── PLAT_BUILD
│   ├── install_scripts
│   ├── med-3.3.1
│   ├── MedCoupling-8.4.0
│   ├── openmpi-3.1.3
│   ├── package_logs
│   ├── packages_targz
│   ├── petsc-3.10.2
│   └── Salome-V8_4_0-univ
├── PLAT_CODES
├── PLAT_THIRD_PARTY
│   ├── hdf5 -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/salome/prerequisites/Hdf5-1814/
│   ├── med -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/med-3.3.1
│   ├── med-3.3.1
│   ├── MED_coupling -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/MedCoupling-8.4.0
│   ├── MedCoupling-8.4.0
│   ├── MED_mod -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/salome/modules/MED_V8_4_0/
│   ├── openmpi -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/openmpi-3.1.3
│   ├── openmpi-3.1.3
│   ├── petsc -> /dsk5/dsk5/platform/PLAT_THIRD_PARTY/petsc-3.10.2/linux-opt
│   ├── petsc-3.10.2
│   └── salome -> /dsk5/dsk5/platform/PLAT_BUILD/Salome-V8_4_0-univ
├── PLAT_USERS
└── PLAT_VISU
    └── appli_salome
====================================






=================================================                      
------------------------------------------------
4A InstCodes
------------------------------------------------
=================================================


=================================================          
4A1)  libmesh
=================================================          



=================================================          
4A2) femus
=================================================          





=================================================          
4A3) OpenFoam
=================================================          


