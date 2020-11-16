**Index by title**

  * [About this wiki](https://github.com/Venkat004/nmag/wiki/FullWiki#about-this-wiki)
  * [Bugfix1](https://github.com/Venkat004/nmag/wiki/FullWiki#patch-to-fix-a-bug-arising-when-dealing-with-periodic-systems)
  * [Bug report](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#reporting-a-bug-to-the-nmag-developers)
  * [Compile cblaslapack](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#compile-nmag-with-blaslapack-versions-downloaded-automatically-by-petsc)
  * [Granular media](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#granular-media)
  * [Hlib issues](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#what-to-do-if-compilation-of-hlib-fails)
  * [H change in t](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#user-query-can-i-have-an-applied-field-changing-both-in-time-and-in-space)
  * [Import from salome](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#script-to-import-unv-mesh-from-salome-platform)
  * [Installing netgen](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#installing-netgen-from-source-on-ubuntu-104-or-debian-60-squeeze)
  * [Installing scipy](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#installing-scipy)
  * [Install fedora14x64](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#how-to-install-nmag-01-beta-6481-on-fedora-14-64-bit)
  * [Iridis3](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#compiling-nmag-on-iridis-3)
  * [Magnetization along a curve ](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#probing-the-magnetization-along-a-curve-as-a-function-of-space-and-time)
  * [Multiarch problems](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#compilation-of-nmag-on-ubuntu-1104-and-possibly-recent-systems)
  * [Nmag cheat sheet](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#nmag-cheat-sheet)
  * [Nmag Wiki](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#nmag-wiki)
  * [Ocaml 3 11 1](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#compiling-nmag-with-ocaml-3111)
  * [Performance data](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#performance-data)
  * [Probing the magnetization along a curve as a function of space and time ](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#probing-the-magnetization-along-a-curve-as-a-function-of-space-and-time-1)
  * [Recompile nmag](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#recompiling-nmag-after-a-change-in-the-source)
  * [Resampling](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#resampling)
  * [Salome as cad form mesh](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#using-salome-as-a-cad-tool-for-creating-complex-meshes)
  * [Save in different dir](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#save-data-in-arbitrary-directory)
  * [Sim convergence](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#how-to-check-the-convergence-of-the-simulation)
  * [Snowleopard](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#compiling-on-mac-os-x-snow-leopard)
  * [User contrib](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#user-contributed-content)
  * [User contrib example](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#example-of-user-provided-content)
  * [Using Gmsh](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#using-gmsh)
  * [Visualise diff](https://github.com/Venkat004/nmag/wiki/FullWiki/_edit#how-to-visualise-the-difference-between-two-fields-defined-over-the-same)

* * *

# About this wiki¶

This Nmag Wiki is world visible. It is more dynamic than the Nmag manual and
provides recipes for some simulations scenarios that are not (yet) captured in
the Nmag manual
([html](http://nmag.soton.ac.uk/nmag/current/manual/html/manual.html)).

We do invite and welcome contributions from users (full recipes into the "User
contributed section", corrections are welcome anywhere). Currently, we ask you
[to register](https://152.78.138.239/community/account/register) and to let us
know subsequently by email that you have done so
([nmag@soton.ac.uk](mailto:nmag@soton.ac.uk)) so that we can activate your
account.

* * *

# Patch to fix a bug arising when dealing with periodic systems¶

The last released version of Nmag (0.1 beta (6481)) is affected by a bug which
emerges when simulating a periodic system (see this [example in the
manual](http://nmag.soton.ac.uk/nmag/0.1/manual/html/manual.html#example-spin-
waves-in-periodic-system)). The issue appears when saving data to file and
leads to the interruption of the simulation with the following error messages:

    
    
    [...]
    File "/home/username/src/nmag-0.1/lib/python2.6/site-packages/tables/carray.py",
    line 191, in __init__
      % type(atom)
    ValueError: atom parameter should be an instance of tables.Atom and you passed a <type 'tuple'>.
    

To solve the issue you should download the [following
file](http://dl.dropbox.com/u/1820549/soton/nmag/hdf5_v01.py) and use it to
replace the file `nmag-0.1/nsim/interface/nfem/hdf5_v01.py`. For example,

    
    
    cd nmag-0.1 # Enter the directory where Nmag is
    wget http://dl.dropbox.com/u/1820549/soton/nmag/hdf5_v01.py
    cp hdf5_v01.py nsim/interface/nfem/hdf5_v01.py
    

Here we use `wget` to download the file from the command line, we then use
`cp` to transfer the file to the proper location. You may achieve the same
effect in a different way (downloading the file with your browser and copying
to the right location).

This should solve the issue.

* * *

# Reporting a bug to the Nmag developers¶

## Create a bug report¶

We created a script to collect information about your system and the problems
Nmag may have encountered. If you are using the release candidate then this
script can be found in the main directory of the distribution, and has the
name `build_bug_report`. If you are using the old, officially released,
version, then this file is not present and you need to download by clicking
[here](http://dl.dropbox.com/u/1820549/soton/nmag/build-bug-report). You
should place the file under the directory containing the nmag distribution
(typically named `nmag-0.1`).

For example,

    
    
    cd nmag-0.1
    mv ~/Downloads/build_bug_report .
    

(here it is assumed that you saved the file in the folder `~/Downloads`)

Now you should just run the script (from the directory `nmag-0.1`):

    
    bash build_bug_report

The script should generate a file named `bug-report.tgz`.

Please send it together with a description of the problem to the Nmag
developers.

* * *

# Compile Nmag with BLAS/LAPACK versions downloaded automatically by PETSc¶

This is a contribution from Gilles Nguyen from the University of Brest
(France):

To compile nmag :

1. you should compile Nmag using GCC. If you are in a cluster, you may then
have to disable using the Intel C compiler, by commenting in your .cshrc (or
equivalent) the line `module intel` (otherwise, the header files for Intel
compiler are selected during compilation, leading to compilation errors each
time the headers are included with #include<...> (because using <...> instead
of using "..." commands to the preprocessor to find the header files in the
environment paths which depend to the modules used)

2. add in the Makefile:

    
    
      PETSC_MORE_CONFIG_OPTS=-COPTFLAGS=$(COPTFLAGS) -CXXOPTFLAGS=$(COPTFLAGS) --download-c-blas-lapack=1
    

as mentioned when the compilation error prompted to do this.

3. make uninstall

4 - make The option `"--download-c-blas-lapack=1"` downloads effectively the C
source files of the libraries blas et lapack in
"nmag-0.1/lib/petsc/externalpackages/f2cblaslapack". It seems that they are
detected as they were already compiled. But they are in fact not compiled.

The error is probably due to the file "BlasLapack.py" in
"/lib/petsc/python/BuildSystem/config/packages/":

    
    
       if os.path.isfile(os.path.join(libdir,'tmpmakefile')) and
                         (SourceDB.getChecksum(os.path.join(libdir,'tmpmakefile'))
                         == SourceDB.getChecksum(os.path.join(blasDir,'tmpmakefile'))):
          self.framework.log.write('Do not need to compile '+l +'blaslapack, already compiled\n')
          return libdir  <<<<<<<<
    

5 - So after, we compile the libraries with "tmpmakefile" : `make -f
tmpmakefile`

6- After, we add in the "Makefile" the path where the librairy files could be
found:

    
    
    
    PETSC_MORE_CONFIG_OPTS=-COPTFLAGS=$(COPTFLAGS) -CXXOPTFLAGS=$(COPTFLAGS) --with-blas-lapack-dir=/home3/caparmor/gnguyen/Gilles/nmag/nmag-0.1/lib/petsc/externalpackages/f2cblaslapack
    

* * *

# Granular media¶

## Overview¶

The scripts on this page are intended as a starting point to allow users to
create their own granular-like meshes for use with Nmag. Although both scripts
should be fully functional as they are, it is likely they will need amending
for each particular case. There are two different programs, both written in
Python, one which creates an array of ellipsoids using Netgen and the other
creates a Voronoi-cell type arrangement of grains. Both programs have very
similar input syntaxes.

## Ellipsoid Builder¶

This program creates an array of meshed ellipsoids using Netgen. The program
has many variables which can be selected from the command line; the full list
of which can be found by running `EllipsoidBuilder.py --help` or reading the
source code.

### Download¶

[Download here](https://www.dropbox.com/sh/gifwko3dh6yplqj/vV4ladlO-v)

This Dropbox page has the EllipsoidBuilder.py script, combined with a sample
output which was used to make the image below for reference.

### Prerequisites¶

  * Python 2.x
  * Netgen [http://www.hpfem.jku.at/netgen/](http://www.hpfem.jku.at/netgen/)

### Output¶

Once successfully run, the program outputs a selection of files as follows
(assuming the chosen filename was `Ellipsoids`):

  * `Ellipsoids.py` - skeleton Python Nmag script with the material and meshes defined (needs actual simulation code to be written manually, e.g. to define a hysteresis loop etc.)
  * `Ellipsoids.geo` - geometry file read by Netgen
  * `Ellipsoids.neutral` - 'neutral' file which is the mesh output from Netgen
  * `Ellipsoids.nmesh.h5` - the mesh file once interpreted and compressed using `nmeshimport`

A meshed output can be seen in the image below.

![](https://dl.dropbox.com/sh/gifwko3dh6yplqj/0fdIZK_GRJ/Ellipsoids.jpg?dl=1)

This was created using the default values in the script with 5 rows and 10
columns. Note that the script introduces randomness in the ellipsoid
orientation by default.

### Known Issues¶

On some installations, calling `netgen` will not start Netgen. The reference
to Netgen at the bottom of the script may have to be changed to
`/opt/netgen/bin/netgen` or a symbolic link or similar created.

## Voronoi Builder¶

This program creates and array of extruded Voronoi cells using Gmsh which can
be used to simulate a granular medium in Nmag. The program has many variables
which can be selected from the command line; the full list of which can be
found by running `VoronoiBuilder.py --help` or reading the source code. Unlike
the Ellipsoid Builder script, this program does not automatically mesh the
geometry. Instead, the `.geo` file must be opened in Gmsh and meshed manually.

### Download¶

[Download here](https://www.dropbox.com/sh/frxdsc1zksw9wb6/_izvTs5pBP)

This Dropbox page has the VoronoiBuilder.py script, combined with a sample
output which was used to make the images below for reference.

### Prerequisites¶

  * Python 2.6
  * Gmsh [http://geuz.org/gmsh/](http://geuz.org/gmsh/)
  * Qhull [http://qhull.org](http://qhull.org)

### Output¶

Once successfully run, the program outputs a selection of files as follows
(assuming the chosen filename was `Voronoi`):

  * `Voronoi.py` - skeleton Python Nmag script with the material and meshes defined (needs actual simulation code to be written manually, e.g. to define a hysteresis loop etc.)
  * `Voronoi.geo` - geometry file read by Gmsh

A meshed output can be seen in the images below.

![](https://dl.dropbox.com/s/qcq3foj1y7m7se5/voronoi_1.jpg?dl=1)

![](https://dl.dropbox.com/s/iekq1s6ai620011/voronoi_2.jpg?dl=1)

This was created using the default values in the script with 5 rows and 10
columns. Note that the script introduces randomness in the cell boundary
position by default.

* * *

# What to do if compilation of HLib fails¶

If the compilation of HLib fails with the error:

    
    
    ...
    ...
    checking for BLAS in VecLib... no
    checking for g77 BLAS... no
    checking for g77 BLAS with pthread... no
    checking for gfortran BLAS... no
    configure: error: Cannot find BLAS
    make[1]: *** [.deps_hlib_configure] Error 1
    make[1]: Leaving directory `/home/guru/Downloads/nmag-0.1'
    make: ***
    [nsim/interface/extra/lib/libhmatrix-1.3.so<http://libhmatrix-1.3.so><http://libhmatrix-1.3.so>]
    Error 2
    

Try to install liblas-dev, libgfortran and gfortran.

* * *

# User query: Can I have an applied field changing both in time and in space?¶

You can simulate an applied field which both changes in space and time: this
may be useful to mimic the effect of a write head on the magnetic grains of an
hard disk while the head is moving.

The way we do this is by changing the applied field every delta_t picoseconds.
This means that the applied field won't change continuously in time: it will
be piecewise constant in time (but, in general, it can be non uniform in
space).

You can do something like that:

    
     1 import math
     2 
     3 def set_H(sim):
     4   width = 10.0        # nm
     5   v = 100.0           # nm/ns == m/s
     6   H_amplitude = 0.5e6 # A/m
     7 
     8   t = float(sim.time/SI(1e-9, 's')) # get the time in ns
     9   center = (v*t, 0, 0) # center of the applied field region
    **10**   def H(r):
    11     x, y, z = [ri/1e-9 - ci for ri, ci in zip(r, center)] 
    12     factor = H_amplitude*math.exp(-(x*x + y*y + z*z)/(width*width))
    13     return [factor, factor, factor]
    14 
    15   sim.set_H_ext(H, unit=SI('A/m'))
    16 
    17 sim.relax(do=[(set_H, every('time', SI(50e-12, 's'))),
    18               ('exit', at('time', SI(1000e-12, 's')))])
    

The function set_H is called every 50 ps and does the following: it sets a new
field from the function H(r).

This function sets a field which directed along the direction [1, 1, 1] and
almost vanishes outside a sphere with radius ~ 30.0 nm.

The center of this sphere moves along the direction [1, 0, 0] with velocity
100 nm/ns, thus simulating the motion of a write head in a hard disk.

Obviously the piece of code is not complete, it shows only the technique in
order to have a field changing in time and space.

For a complete example see the next section.

## Complete example: simple moving write-head example¶

Here is a simulation of five cubes made of cobalt and a write-head which moves
on the top of the cubes and applies a time-varying field in order to change
their magnetisation. At the beginning the magnetisation of all the cubes is
pointing in the [0, 0, 1] direction. After the write-head has passed over the
cubes, the magnetisation of cube 1, 3 and 5 are switched in the opposite
direction, while cube 2 and 4 have unchanged magnetisation.

This is possible because the write-head field, which is space-dependent (being
intense only inside a sphere of radius 15-20 nm), changes also in time. It
indeed translates in space, but also change in intensity, being directed in
the [0, 0, -1] direction when the sphere is at the center of cube 1, 3 and 5
and in the [0, 0, 1] direction when the center of the sphere is in cube 2 and
4.

Here is the geo file used to generate the mesh (Netgen):

    
    
    algebraic3d
    
    # cubes
    solid cube1 = orthobrick (    0, 0, 0;  20.0, 20.0, 20.0) -maxh = 2;
    solid cube2 = orthobrick ( 30.0, 0, 0;  50.0, 20.0, 20.0) -maxh = 2;
    solid cube3 = orthobrick ( 60.0, 0, 0;  80.0, 20.0, 20.0) -maxh = 2;
    solid cube4 = orthobrick ( 90.0, 0, 0; 110.0, 20.0, 20.0) -maxh = 2;
    solid cube5 = orthobrick (120.0, 0, 0; 140.0, 20.0, 20.0) -maxh = 2;
    
    tlo cube1;
    tlo cube2;
    tlo cube3;
    tlo cube4;
    tlo cube5;
    

And here is the full listing of the example:

    
     1 from nmag.common import *
     2 import math
     3 
     4 # Define magnetic material (data from OOMMF materials file)
     5 mat_Co = MagMaterial(name="Co",
     6                      Ms=SI(1400e3, "A/m"),
     7                      exchange_coupling=SI(30e-12, "J/m"),
     8                      anisotropy=uniaxial_anisotropy(axis=[0, 0, 1],
     9                                                     K1=SI(520e3, "J/m^3")))
    **10** sim = Simulation()
    11 sim.load_mesh("cubes.nmesh.h5",
    12               [('cube1', mat_Co), ('cube2', mat_Co), ('cube3', mat_Co),
    13                ('cube4', mat_Co), ('cube5', mat_Co)],
    14               unit_length=SI(1e-9, 'm'))
    15 
    16 sim.set_m([0, 0, 1])
    17 
    18 sim.relax(save=[('fields', at('convergence'))])
    19 
    **20** t0 = [sim.time]
    21 
    22 def set_H(sim):
    23     t = float((sim.time - t0[0])/SI(1e-9, 's'))  # get time in ns
    24     width = 10.0                                 # nm
    25     v = 25.0                                     # nm/ns = m/s
    26     H_amplitude = 4.0e6*math.sin(math.pi*t)      # A/m
    27     center = (v*t, 20, 10)
    28     print "CENTER IN", center
    29     def H(r):
    **30**         x, y, z = [ri/1e-9 - ci for ri, ci in zip(r, center)]
    31         factor = H_amplitude*math.exp(-(x*x + y*y + z*z)/(width*width))
    32         return [0, 0, -factor]
    33 
    34     sim.set_H_ext(H, unit=SI('A/m'))
    35 
    36 set_H(sim)
    37 
    38 sim.set_params(stopping_dm_dt=0*degrees_per_ns)
    39 
    **40** sim.relax(save=[('fields', every('time', SI(200e-12, 's'), first=t0[0]))],
    41           do=[(set_H, every('time', SI(50e-12, 's'), first=t0[0])),
    42               ('exit', at('time', SI(6000e-12, 's')))])
    

Here is the magnetisation at the beginning of the simulation, after the first
relax command (whose purpose is just to find the zero field magnetisation
configuration):

![](http://dl.dropbox.com/u/1820549/before.png)

and here is the magnetisation after the write-head has passed over the cubes:

![](http://dl.dropbox.com/u/1820549/after.png)

* * *

# Script to import .unv mesh from Salome platform¶

Here is a contribution from Luyang Han.

Hello all,

This is an ad-hoc script to import the .unv mesh file exported from Salome
platform ([http://www.salome-platform.org/](http://www.salome-platform.org/)).
The solid modeling and mesh generation in Salome is much more powerful and
easier to use compared to gmsh.

Salome can only export unv file with just one region, thus all simplices are
set to region 1.

To use the script do:

    
    
    chmod +x importunv.py
    ./importunv.py infile.unv outfile.nmesh.h5
    

The script need to setup nmag path in the env.

Regards.

    
    
    #!/usr/bin/env nsim
    
    import sys
    
    import nmesh
    
    def loadmesh(filename):
      vertices = []
      simplex = []
      with open(filename) as fname:
          #skip the first two lines
          fname.readline()
          fname.readline()
          # start to read the vertices
          input_a = fname.readline()
          input_b = fname.readline()
          while input_a.strip() <> '-1' :
              coord = map(float,input_b.strip().split())
              vertices.append(coord)
              input_a = fname.readline()
              input_b = fname.readline()
          # finish the vertices part.
          # ignore one line here
          fname.readline()
          # read lines till we reach the simplex region
          input_a = fname.readline()
          while True:
              if len(input_a.strip().split()) == 6 and input_a.strip().split()[-1] == '4':
                  break
              else:
                  input_a = fname.readline()
          # now we reached the first line of the simplex region
          #input_b = fname.readline()
          #simp = map(int,input_b.strip().split())
          #simplex.append(simp)
          #input_a = fname.readline()
          while input_a.strip() <> '-1' :
              input_b = fname.readline()
              simp = map(int,input_b.strip().split())
              simplex.append(simp)
              input_a = fname.readline()
    
      # finish the reading
      return vertices, simplex
    
    #main program
    mesh = None
    
    infile = sys.argv[1]
    outfile = sys.argv[2]
    
    points,simplices_indices = loadmesh(infile)
    
    simplices_regions = [1] * len(simplices_indices)
    
    mesh = nmesh.mesh_from_points_and_simplices(points=points, simplices_indices=simplices_indices, simplices_regions=simplices_regions, periodic_point_indices=[], initial=1, do_reorder=True)
    
    mesh.save(outfile)
    

* * *

# Installing Netgen from source on Ubuntu 10.4 (or Debian 6.0 Squeeze)¶

In this example we do everything inside the directory `~/src` (`~` is a common
shell convention to refer to your home directory, it is typically expanded to
something like `/home/yourusername`). You can create the directory with:

    
    
    cd ~
    mkdir src # create the directory, in case it does not exist, yet
    

## Requirements¶

You will need to install a number of packages in order to compile Netgen
correctly. You can do it with just one line from your shell:

    
    
    sudo aptitude install tcl-dev tk-dev tix-dev libxmu-dev
    

Notice that you will need administrator priviledges in order to do that.

You may need to also install `libglut-dev` and `g++` (at least on a clean
Debian 6.0 Squeeze installation).

## Installing Togl from sources¶

There is a further requirement which is not available in the Ubuntu
repositories. You'll then have to install it by hand. First let's download the
package:

    
    
    cd ~/src
    wget http://sourceforge.net/projects/togl/files/Togl/1.7/Togl-1.7.tar.gz/download
    tar xzvf Togl-1.7.tar.gz
    

Now enter the directory, configure, compile and install.

    
    
    cd ~/src/Togl-1.7
    ./configure
    make
    sudo make install
    

The last command will require to enter your password (and require you to be an
administrator). If everything went as it should, typing the command `ls
/usr/lib/Togl-1.7` should produce the following output:

    
    
    libTogl1.7.so  pkgIndex.tcl
    

## Installing Netgen from sources¶

Download the latest Netgen tarball and unpack it under the `~/src` directory.

    
    
    cd ~/src
    wget http://kent.dl.sourceforge.net/project/netgen-mesher/netgen-mesher/4.9.13/netgen-4.9.13.zip
    unzip netgen-4.9.13
    cd netgen-4.9.13
    

Configure, compile and install it:

    
    
    ./configure
    make
    sudo make install
    

That will create a directory under `/opt`. Now get back to the `~/src`
directory and download a file like this:

    
    
    cd ~/src
    wget http://dl.dropbox.com/u/1820549/soton/netgen
    

The file should have the following content:

    
    
    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/Togl1.7
    export NETGENDIR=/opt/netgen/bin
    /opt/netgen/bin/netgen "$@" 
    

Copy the file in the `/usr/bin` directory and adjust the permissions with the
following two commands:

    
    
    sudo cp netgen /usr/bin
    sudo chmod a+x /usr/bin/netgen
    

You should now be able to launch Netgen from the command line:

    
    
    you@machine:~$ netgen &
    [1] 15400
    you@machine:~$ NETGEN-4.9.13
    Developed at RWTH Aachen University, Germany
    and Johannes Kepler University Linz, Austria
    Parsing ng.tcl                                                                                
    optfile ./ng.opt does not exist - using default values
    

* * *

# Introduction¶

Once you have compiled Nmag from sources, you may want to add some extra
packages to the Python installation which comes with it. Indeed, Nmag does not
use the Python installed on your system (if there is one), but rather brings
its own Python interpreter, meaning that any other extra Python library has to
be compiled expressly for it. In other words, when you launch `nsim` you won't
be able to import the libraries that you installed on your system Python.
While this is certainly inconvenient, it allows us to distribute one unique
file (`nmag-0.1.tar.gz`) which is likely to compile with little trouble on
most Linux distributions.

# Installing SciPy¶

First, compile Nmag from sources.

Second, make sure you have installed the following packages:

  * a sane build environment (which you already have, since you managed to compile Nmag)
  * Swig
  * a Fortran compiler

Indeed, the compilation of SciPy requires such packages to be installed on
your system. Install all of them using the most convenient tool for your
distribution. Download SciPy from the official website. You can do it with
your browser by clicking [here](http://sourceforge.net/projects/scipy/files/sc
ipy/0.7.2/scipy-0.7.2.tar.gz/download). You should save the file into the
directory `nmag-0.1/pkgs/`. Then untar the package:

    
    
    cd nmag-0.1
    tar xzvf pkgs/scipy-?.?.?.tar.gz
    

Now enter the directory created by the tar command and build SciPy:

    
    
    . exports.bash
    cd scipy-?.?.?
    ../bin/python setup.py install
    

The first line modifies the environment such that the local installed
libraries can be found.

Be careful to use `../bin/python` (the Python which comes with Nmag) rather
than simply `python` (the Python installed on your system).

If all goes well than you should be able to import scipy:

    
    
    cd .. # cd into the nmag-0.1 directory
    ./bin/nsim 
    import scipy
    

You should get a silent prompt (no error messages). Exit nsim pressing CTRL+D
or typing exit().

* * *

# How to install Nmag 0.1 beta (6481) on Fedora 14 (64 bit)¶

Wagner de Oliveira da Rosa explains how he installed Nmag on Fedora 14. Note
that newer versions should not require this hack.

Here is his mail:

How to install nmag on Fedora 14 - 64 bits using the method A (compiling all
from the source):

1 - Download the nmag source file from the developers webpage
nmag-0.1-all.tar.gz

2 - Install all the libraries and compilers needed like gawk, gcc, gfortran,
readline, blas, lapack, etc (see the instruction manual)

3 - To compile the code from the source, you need to locate the library
libutil.so using the follow command in terminal:

    
    
    $ locate libutil.so
    

This search it will produce a result like this:

    
    
    /lib64/libutil.so.1
    /usr/lib64/libutil.so 
    

4 - Once located the `libutil.so` path, now we should go into the nmag main
directory (where you untarred the files) and create a link to this file as
shown below:

    
    
    cd nmag-0.1 # directory where you untarred nmag
    cd lib
    ln -s /usr/lib64/libutil.so # you should replace with whatever you got from your system (from the locate command)
    

5 - Then, after all, do as follows:

    
    
    cd .. # go back to the nmag main directory
    make
    

6 - From now, nmag should compile without any problems. However, before you
get set and start any simulation, you should proceed as follows. Find the file
`ldflags.bash`, under the directory `nmag-0.1/nsim/bin/` (`nmag-0.1` is the
main nmag directory). Open it using your preferred text editor and append this
line to the end of the file

    
    
    export LD_PRELOAD=/usr/lib64/libz.so
    

where `/usr/lib64/libz.so` should be replaced with the correct path to the
`libz.so` library in your system (you can use `locate libz.so` to determine
this, as done in step 3).

7 - Now that you will force to load the lib.so the nmag should be ready to
use. You can try it by typing in terminal:

    
    
    $ nsim
    >>>
    

If you got this the nmag and nsim were successfully compiled and they are
ready to use.

Have a nice simulation!!!

* * *

# Compiling Nmag on Iridis 3¶

On Iridis 3 the compilation of Nmag is complicated by the fact that one has to
use the Intel provided versions of BLAS/LAPACK. On the other hand, such
libraries are able to exploit the hardware of the machine and should allow
Nmag to use the multi-core architecture of the CPUs.

## Using Intel Math Kernel Library (MKL)¶

To compile against the Intel MKL one has to load the appropriate module on
Iridis 3.

Login on Iridis 3, `ssh yourusername@iridis3_a.soton.ac.uk` and type:

    
    
    module load intel/mkl
    

Documentation for the library can be found by typing:

    
    
    mkl_ref
    mkl_use
    

These are two shell scripts launching acrobat reader with the appropriate path
for the PDF files.

Try `less `which mkl_ref`` and `less `which mkl_use``.

In theory you could now compile Nmag, download the tarball, place it somewhere
on the system

## PETSc¶

Note that PETSc configuration may fail due to a problem with python and
libssl.so (which on Iridis3 does reference a symbol, `pqueue_size`, which is
not defined anywhere). If you have this problem, then jump to the section
about Python later before reading this one.

For PETSc 2.3.3-p15 the following works:

    
    
    python ./config/configure.py --with-shared \
     --with-mpi-dir=/temp/franchin/i3/nmag-0.1/lib/mpich2 \
     --COPTFLAGS=-O3 --CXXOPTFLAGS=-O3 --with-debugging=no \
     --with-blas-lapack-lib="-L/local/software/intel/mkl/10.2.1.017/lib/em64t -lmkl_intel_lp64 -lmkl_sequential -lmkl_core -lpthread -lm" 
    

While for PETSc 3.1-p5 the following works:

    
    
    python ./config/configure.py --with-shared --with-single-library=1 \
     --with-mpi-dir=/temp/franchin/i3/nmag-0.1/lib/mpich2 \
     --COPTFLAGS=-O3 --CXXOPTFLAGS=-O3 --with-debugging=no \
     --with-blas-lapack-lib="" --LDFLAGS="-L/local/software/intel/mkl/10.2.1.017/lib/em64t -lmkl_intel_lp64 -lmkl_sequential -lmkl_core -lpthread -lm" 
    

## HLib¶

To configure HLib:

With sequential MKL:

    
    
    ./configure --with-blas-ldflags='-lm -L/local/software/intel/mkl/10.2.1.017/lib/em64t -lmkl_intel_lp64 -lmkl_sequential -lmkl_core -lpthread' --prefix=/home/franchin/nmag-0.1/nsim/interface/extra'
    

With parallel MKL:

    
    
    ./configure --prefix=/work/franchin/par/nmag-0.1/nsim/interface/extra --with-blas-ldflags="-L/local/software/intel/mkl/10.2.1.017/lib/em64t -lmkl_intel_lp64 -lmkl_gnu_thread -lmkl_core -liomp5 -lm -lpthread" 
    

## Python¶

If compilation of Python fails, do as follows. First, Iridis 3 has its own
version of Python, in particular what we need is Python 2.6 or above. Get it
from Iridis:

    
    
    cd nmag-0.1
    cp /local/software/rh53/python/2.6.5/source/Python-2.6.5.tar pkgs/
    

Now adjust the package (it looks as a .tar file but it actually isn't, it is a
zipped tar file):

    
    
    cd nmag-0.1/pkgs
    mv Python-2.6.5.tar Python-2.6.5.tar.gz
    gunzip Python-2.6.5.tar.gz
    bzip2 Python-2.6.5.tar
    

Now change the `nmag-0.1/Makefile` so that it uses this file. Type `make`.
Python 2.6.5 should be compiled. PETSc is the next to be compiled and it
fails. Indeed, Iridis 3 is apparently broken: the symbol pqueue_size in
libssl.so is not defined anywhere else (at least at the time of writing) and
this makes it impossible to import modules such as md5 or hashlib. No worries,
Iridis 3 has its own python2.6 (apparently it has been compiled before the
package damage) we can steal it.

    
    
    cd nmag-0.1/lib
    mv python2.6 old-python2.6
    cp -r /local/software/rh53/python/2.6.5/gcc/lib/python2.6 .
    

Now your local python almost works, but you still needs some adjustments:

    
    
    cd nmag-0.1/lib
    cp old-python2.6/config/libpython2.6.a python2.6/config/
    # ^^^ This is needed because the Iridis 3 guys didn't use --enable-shared when configuring
    cp old-python2.6/config/Makefile python2.6/config/
    # ^^^ This will let python compile new modules appropriately
    

You now have your own working copy of Python 2.6. Note that you cannot easily
use the Iridis 3 Python, as it doesn't have pytables (and maybe other
modules). This is why here we build our own version of Python, so that we can
install on it whatever we want.

Note that Python >= 2.6 is necessary, since Nmag is using syntax features
which are not present in Python 2.4. Now you can use Python to compile PETSc
and Nmag.

## libutils.so¶

You may also have to do the following in order for the pycaml module to
compile correctly

    
    
    cd nmag-0.1/lib
    ln -s /usr/lib64/libutil.so .
    

Indeed, in order to link against libpython one also needs to link against
libutil (sometimes), which is not stored inside `/usr/lib` for some reasons...

* * *

# Probing the magnetization, along a curve, as a function of space and time¶

This is to describe how to probe the magnetization, from the h5 file, along a
circular arc. The arc may be replaced with any geometric curve.

Once the magnetization has been obtained it may be Fourier transformed in
order to obtain the dispersion.

This script should be saved as probe.py and then run with the following
command:

nsim <path to the .h5 file> <file in which the probed magnetization is to be
saved>

    
    
    
    #Import some libraries
    import math
    import sys
    
    import ocaml
    from nmag.h5probe import Fields
    from nmag import float_set
    
    from numpy import pi, linspace, cos, sin, subtract, savetxt, size
    
    # First we obtain the handler for the fields
    handler = Fields(sys.argv[1])
    
    #probing along a 90 degree (45 degrees on both sides from the centre) arc along a circle of radius 550 nm and at z=0
    angle = float_set([3*pi/4.0, [100], pi/4.0])
    R=550
    xs=R*cos(angle)
    ys=R*sin(angle)
    
    #idlist to give different instances of time
    idlist=range(0,10241,1)    
    
    #Declare some lists for saving purposes
    vs = []
    minit=[];mlist=[]
    
    #loading the 0th time step field; The '0' corresponds to the id and not a time value
    field = handler.set_field_data("m", "Py", 0)
    
    #Calculating the field along the arc for the 0th time step; it has to be subtracted from every other time step
    
    for i in range(size(xs)):
        minit.append(ocaml.probe_field(field, "m_Py", [xs[i], ys[i], 0.0])[0][1][1])
    
    #For each time (id) step, the field along the arc is calculated and
    #the field at the 0th time step is deducted. This field is then appended to a file
    for t in idlist:
        field = handler.set_field_data("m", "Py", t)
          vs=[]
        for i in range(size(xs)):
            vs.append(ocaml.probe_field(field, "m_Py", [xs[i], ys[i], 0.0])[0][1][1]);
        for num in range(size(xs)):
            mlist.append(subtract(vs, minit)[num])
    
    savetxt(sys.argv[1], mlist)
    
    

* * *

# Compilation of Nmag on Ubuntu 11.04 (and possibly recent systems)¶

## Details about the issue¶

Starting from Ubuntu 11.04, there have been modifications in the path layout
conventions (filesystem hierarchy) to enhance support for different
architectures (details are given here [https://wiki.ubuntu.com/MultiarchSpec](
https://wiki.ubuntu.com/MultiarchSpec)). In particular, some system libraries
have been moved into a directories like `/usr/lib/x86_64-linux-gnu` or
`/lib/x86_64-linux-gnu`. These directories contain libraries which have been
compiled targeting specific architectures. This change confuses some of the
packages we are currently installing in the tarball. In particular, the Python
tables modules, the zlib Python module do not manage to find `libz.so` and are
not compiled properly. This leads to failures when loading and saving data in
Nmag scripts.

You may try to follow the instructions below, while we work on providing a
patch to solve the problem.

## How to solve it¶

First, you should locate where your libz.so library is. Type `locate libz.so`,
you'll get something like:

    
    
    /lib/x86_64-linux-gnu/libz.so.1
    /lib/x86_64-linux-gnu/libz.so.1.2.3.4
    /usr/lib/x86_64-linux-gnu/libz.so
    /usr/lib32/libz.so.1
    /usr/lib32/libz.so.1.2.3.4
    

Our candidate is `/usr/lib/x86_64-linux-gnu/libz.so` we should then do as
follows:

    
    
    cd nmag-0.1.1
    echo 'export LD_PRELOAD="/usr/lib/x86_64-linux-gnu/libz.so"' >> nsim/bin/ldflags.bash
    

In the line above you should substitute `/usr/lib/x86_64-linux-gnu/libz.so`
with what is appropriate for your system (given as an output of the `locate`
command).

* * *

  * Nmag cheat sheet
  * Mesh generation
  * Convert from one mesh format to the other
  * Inspect and visualise mesh
  * Running simulations
  * Running MPI simulations
  * Visualise mesh partitioning
  * Postprocessing data

## Nmag cheat sheet¶

### Mesh generation¶

  * Create mesh with Netgen from command line (Geometry specification to Neutral Mesh)  

    
    netgen -geofile=in.geo -moderate -meshfiletype="Neutral Format" \
           -meshfile=out.neu -batchmode

### Convert from one mesh format to the other¶

  * Neutral format (Netgen) to Nmag format:  

    
    nmeshimport --netgen in.neu out.nmesh.h5
    nmeshimport --netgen in.neu out.nmesh

  * Binary Nmag format to ASCII Nmag format and viceversa:  

    
    nmeshpp -c in.nmesh.h5 out.nmesh
    nmeshpp -c in.nmesh out.nmesh.h5

  * Binary Nmag format to AVS format (Magpar):  

    
    nmeshpp -m in.nmesh.h5 out.inp

### Inspect and visualise mesh¶

  * Getting generic info on the mesh  

    
    nmeshpp in.nmesh.h5 -i   # show general information, num points, num simplices, etc
    nmeshpp in.nmesh.h5 -a   # show a distribution of lengths of the edges of the simplices
    nmeshpp in.nmesh.h5 -q   # show a distribution of simplex quality
    

  * Transforming the mesh to a VTK file for visualisation (with Mayavi2 or Paraview):  

    
    nmeshpp --vtk in.nmesh.h5 out.vtk

  * Visualising the mesh from the VTK file obtained from command above (using Mayavi2 or Paraview)  

    
    mayavi2 -d out.vtk -m Surface
    paraview --data=out.vtk # click on apply when Paraview windows is shown

### Running simulations¶

  * Run simulation file ``mysim.py``  

    
    nsim mysim.py

  * Run simulation and confirm that existing data files should be overridden  

    
    nsim mysim.py --clean

  * Continue simulation from stage where it was interrupted before (only for hysteresis command)  

    
    nsim mysim.py --restart

### Running MPI simulations¶

  * Start a parallel run (on 2 machines): 
    
    mpirun -np 2 nsim mysim.py

  * For MPICH2 you need to launch the daemon first (not required for Nmag VM as it is using OpenMPI): 
    
    cd nmag-0.1 # here we assume you installed from source
    ~/lib/mpich2/bin/mpd &
    

If you launch `mpd` for the first time take a look at the [instructions in the
manual](http://nmag.soton.ac.uk/nmag/current/manual/html/manual.html#using-
mpich2)

### Visualise mesh partitioning¶

When you run the simulation in parallel you get:

    
    
    ...
    nfem.ocaml:2010-07-26 15:54:50,578    INFO Processor 0: 1065 nodes
    nfem.ocaml:2010-07-26 15:54:50,578    INFO Processor 1: 1052 nodes
    ...
    

These numbers are recorded in the log file (example `simulation_log.log`).

We here assume that your fields are saved in the file `simulation_dat.h5`.

You can produce a VTK file with the partitioning (and visualise it) using:

    
    nmeshpp simulation_dat.h5 --partitioning=[1065,1052] partitioning.vtk
    mayavi2 -d partitioning.vtk -m Surface

### Postprocessing data¶

  * Inspect field data file simulation_dat.h5:  

    
    nmagpp simulation --fieldlist # get the list of field stored inside the file
    nmagpp simulation --idlist    # get the list of the IDs for the stored fields

  * Convert data from `mysim_dat.h5` file to vtk-files with name `myvtk-000000.vtk`, `myvtk-000001.vtk`, etc.  

    
    nmagpp --vtk myvtk.vtk mysim

  * Write VTK files containing **only** the specified fields (faster than command above):  

    
    nmagpp --vtk myvtk.vtk --fields=m,H_demag mysim

  * Visualising data from the VTK obtained above  

    
    mayavi2 -d myvtk-000000.vtk -m Vectors

  * Get a list of fields stored in NDT file `mysim.ndt`  

    
    ncol mysim

  * Get a list of the fields whose name starts with `H` or `H_e`  

    
    ncol mysim H
    ncol mysim H_e

  * Extract external field (spatial average against time) from ``mysim.ndt`` file  

    
    ncol mysim time H_ext_0 H_ext_1 H_ext_2

  * Extract magnetisation against time (with `ncol`) and plot it with `Gnuplot`:  

    
    ncol mysim time m_Py_0 m_Py_1 m_Py_2 > outfile.dat
    gnuplot
    plot "./outfile.dat" u 1:2 t "m_x" w l, "" u 1:3 t "m_y" w l, "" u 1:4 t "m_z" w l
    

* * *

# Nmag Wiki¶

About this Wiki, including: how to contribute

## Release candidate¶

Please find development snapshots at [http://nmag.soton.ac.uk/nmag/snapshots](
http://nmag.soton.ac.uk/nmag/snapshots)

## Recipes, useful info¶

### Old entries that have been included in the Documentation of Nmag-0.2:¶

User query: Applied field changing in time and space

Saving data in directory other than current working one

How to check the convergence of the simulation

How to visualise the difference between two fields defined on the same mesh?

How to reload an h5 file, sample it along arbitrary points and save to VTK

Nmag cheat sheet

Using Gmsh

### User contributed¶

Compile Nmag with BLAS/LAPACK versions downloaded automatically by PETSc

All user contributions...

## Installation issues¶

Reporting a bug to the Nmag developers

What to do if compilation of HLib fails

Compilation of Nmag on Ubuntu 11.04 (and possibly recent systems)

Compiling with OCaml 3.11.1

Compiling on Mac OS X Snow Leopard

Recompiling Nmag after a change in the source

Installing SciPy from source

Installing Netgen from source on Ubuntu 10.4 (or Debian 6.0 Squeeze)

Compiling Nmag on Iridis 3

### User contributed¶

All user contributions...

## Patches¶

Patch to solve a issue arising when dealing with periodic systems

* * *

# Compiling Nmag with OCaml 3.11.1¶

The newer version of the OCaml (3.11.1) compiler introduces two problems with
the compilation of Nmag.

The first is connected with the changes to the Camlp4 preprocessor, which
break version 0.4.0 of ocamlgsl. This can be solved by updating gsl and
ocamlgsl to the latest versions (1.13 for gsl and 0.6.0 for ocamlgsl).
Alternatively the old version of gsl (1.8) can be used together with version
0.5.3 of ocamlgsl.

The second problem has to do with changes in the implementation of OCaml,
which break the code used to find the size of an OCaml data structure, i.e.
the file `nsim/snippets/objsize.c`. The problem can be solved by replacing the
content of the file `nsim/snippets/objsize.c` (or
`nmag-0.1/nsim/snippets/objsize.c` for those who compiled everything from
source) with the following:

    
    
    #include <stdlib.h>
    
    #include <caml/mlvalues.h>
    #include <caml/memory.h>
    #include <caml/alloc.h>
    
    CAMLprim value caml_memory_footprint(value start) {
          CAMLparam1(start);
          CAMLlocal1(res);
          size_t s = 0;
    
          res = caml_alloc_tuple(3);
          Store_field(res, 0, copy_double(s));
          Store_field(res, 1, copy_double(s));
          Store_field(res, 2, copy_double(s));
          CAMLreturn(res);
    }
    

* * *

# Performance data¶

The idea for this webpage is to share information about run times and memory
consumption for various simulations, to help in making assessments as to what
system size can feasibly be computed.

Entries below should contain:

  1. the system geometry 
  2. the total number of nodes (`points`) in the mesh and surface nodes (`boundary points`) (this can be obtained using the ``nmeshpp -i `` command)
  3. the amount of time that has been simulated (i.e. 2ns or such), or how many points in a hysteresis loop have been computed
  4. the amount of RAM that as required (and whether the Hlib has been used)
  5. the amount of time it took to run the simulation (i.e. hours, days, weeks)
  6. the hardware: some info on CPU and clockrate if available  
#.serial or parallel, if parallel: what hardware? MPI on multi-core, multi-CPU
or multi-nodes?

Ideally, the entries should include

  1. a reference to a publication (this can be added later when it becomes available)
  2. the nmag simulation file (maybe for one of the simulations run for this work)
  3. if possible a file to create the mesh if possible (for example a geo file for Netgen)

# Data¶

* * *

# Probing the magnetization, along a curve, as a function of space and time¶

This wiki page describes how to probe the magnetization, from the h5 file,
along a circular arc. The arc may be replaced with any geometric curve.

Once the magnetization has been obtained, it may be Fourier transformed in
order to obtain the dispersion of spin waves.

This script should be saved as a python script (say probe.py) and then run
with the following command:

nsim probe.py <path to the .h5 file> <file in which the probed magnetization
is to be saved>

This has been implemented with Nmag version 0.2.1

    
    
    
    #Import some libraries
    import math
    import sys
    
    import ocaml
    from nmag.h5probe import Fields
    from nmag import float_set
    
    from numpy import pi, linspace, cos, sin, subtract, savetxt, size
    
    # First we obtain the handler for the fields
    handler = Fields(sys.argv[1])
    
    #probing along a 90 degree (45 degrees on both sides from the centre) arc along a circle of radius 550 nm and at z=0
    angle = float_set([3*pi/4.0, [100], pi/4.0])
    R=550
    xs=R*cos(angle)
    ys=R*sin(angle)
    
    #idlist to give different instances of time
    idlist=range(0,10241,1)    
    
    #Declare some lists for saving purposes
    vs = []
    minit=[];mlist=[]
    
    #loading the 0th time step field; The '0' corresponds to the id and not a time value
    field = handler.set_field_data("m", "Py", 0)
    
    #Calculating the field along the arc for the 0th time step; it has to be subtracted from every other time step
    
    for i in range(size(xs)):
        minit.append(ocaml.probe_field(field, "m_Py", [xs[i], ys[i], 0.0])[0][1][1])
    
    #For each time (id) step, the field along the arc is calculated and
    #the field at the 0th time step is deducted. This field is then appended to a file
    for t in idlist:
        field = handler.set_field_data("m", "Py", t)
          vs=[]
        for i in range(size(xs)):
            vs.append(ocaml.probe_field(field, "m_Py", [xs[i], ys[i], 0.0])[0][1][1]);
        for num in range(size(xs)):
            mlist.append(subtract(vs, minit)[num])
    
    savetxt(sys.argv[2], mlist)
    
    

* * *

# Recompiling Nmag after a change in the source¶

(This document refers to the all-source distribution of Nmag.)

Imagine you have changed some files in the source, such as for example
`nmag-0.1/nsim/snippets/snippets.ml` and you want to recompile Nmag.

You can do this as follows:

    
    
    cd nmag-0.1
    rm nsim/config/configuration.inc
    make
    

* * *

# Resampling¶

(Available in Nmag-0.1.0-dev)

You can load an h5 file like this

    
    
    import ocaml
    from nmag.h5probe import Fields
    
    handler = Fields("infile.h5")
    field = handler.set_field_data("m", "Py", 0)
    

And probe one of its fields like this

    
    
    position = [0, 1, 2] # In mesh units (typically is nanometres)
    value = ocaml.probe_field(field, "m_Py", position)[0][1]
    

This way you can create two arrays: `rs` containing an array of points and
`vs` containing the corresponding values.

You can then use pyvtk to generate a VTK file from these:

    
    
    import pyvtk
    
    grid = pyvtk.UnstructuredGrid(rs)
    data = pyvtk.PointData(pyvtk.Vectors(vs))
    v = pyvtk.VtkData(grid, data)
    v.tofile("outfile.vtk")
    

Here is a full example, which probes the magnetisation in the outer skin of a
cylinder, in sections which are not equally spaced.

Notice the usage of the function `float_set` to specify where the sampling
should be denser (originally, here is where a domain wall was).

The script should be used as `nsim probe.py infile.h5 outfile.vtk`

    
    
    import math
    import sys
    
    import pyvtk
    
    import ocaml
    from nmag.h5probe import Fields
    from nmag import float_set
    
    # First we probe the field in the required points
    handler = Fields(sys.argv[1])
    field = handler.set_field_data("m", "Py", 0)
    
    xs = float_set([-150.0, -145.0, [], -15.0, -12.5, [], 15.0, 20.0, [], 50.0])
    angles = float_set([0, [20], 2*math.pi])
    R, R2 = (4.9, 5.1)
    
    rs = []
    vs = []
    for x in xs:
      for angle in angles:
        r = [x, R*math.cos(angle), R*math.sin(angle)]
        rs.append([x, R2*math.cos(angle), R2*math.sin(angle)])
        vs.append(ocaml.probe_field(field, "m_Py", r)[0][1])
    
    # Now we output the values to a VTK file
    grid = pyvtk.UnstructuredGrid(rs)
    data = pyvtk.PointData(pyvtk.Vectors(vs))
    v = pyvtk.VtkData(grid, data)
    v.tofile(sys.argv[2])
    

* * *

# Using Salome as a CAD tool for creating complex meshes¶

Here is a contribution from Hari Srinivas Gorripati. Hari uses Salome as a CAD
(Computer-Aided Design) program to create complex 3D geometries. Salome
creates the surface of the mesh. For complex geometries with many bodies and
many surfaces, the surfaces have to be saved individually to separate STL
files. These files are then loaded with Netgen to create individual meshes for
each of them. The meshes are then merged and exported to the Neutral file
format. Finally, Nmeshpp can be used to import the merged mesh and use it with
Nmag.

Here is Hari's mail:

If this kind of reporting helps others solve problems, I found a work around
how to generate more than one region using NETGEN. I applied this to your cube
problem though your .geo file is the easiest way to go. Following are the
steps for it:

  1. Create the required geometries/objects using Salome (or any other similar software) as you would want it to appear in the final simulation and export them as individual ascii-STL files (Exporting the objects built into a compound with groups didn't work for me here).
  2. Open each exported geometry using NETGEN and generate the mesh. This allows assigning different mesh sizes for different regions. After the mesh was created save all those objects using "File->Save mesh (.vol)" 
  3. Final step is to open one of those files and and then chose "File -> Merge mesh" to merge all the individual files. This would just appear like the one created in Salome in the beginning.

I think this procedure will be good for users who create complex geometries. I
tried this procedure for ".brep" files. It didn't work for me.

* * *

# Save data in arbitrary directory¶

## Do you really need to do so?¶

First, consider whether you really need to save data in a different directory.
Remember that you can run many simulation with one single script just using a
different simulation name, like:

    
    
    ...
    s1 = Simulation('one')
    ...
    s2 = Simulation('two')
    ...
    

When you save the data for simulation one you get files like `one_dat.h5` and
`one_dat.ndt`, while when dealing with simulation two you get `two_dat.h5` and
`two_dat.nd5`. There is no interference between the two simulation, which may
be the main reason why you may be reading this part of the Nsim documentation.

## Here is how you do it¶

When you run a simulation script which saves data from a simulation, you get
that the files are saved in the current working directory.

In order to change this and save data into a directory called `./mydir/` you
should start your script in the following way:

    
    
    import nmag
    import nsim.features
    fts = nsim.features.Features()
    fts.set('etc', 'savedir', './mydir/')
    ...
    ...
    

Alternatively, you can change the current working directory at the beginning
of the file with ordinary Python code:

    
    
    import os
    initial_dir = os.path.abspath(os.path.curdir)
    os.chdir('./mydir')
    ...
    ...
    os.chdir(initial_dir)
    

If the directory you want to write to does not exist then (in both the two
example) you may have to create it first, with something like:

    
    
    the_dir = './mydir'
    import os
    if not os.path.exists(the_dir):
      os.mkdir(the_dir)
    

* * *

# How to check the convergence of the simulation¶

How long it takes to run a simulation? This depends very much on what you are
simulating and under what conditions (applied field, current, etc). Sometimes,
however, your simulation may not be ending quickly as you expected and you may
want to check what is happening. It may be, indeed, that the simulation is not
converging, which means that it may actually never end. One thing you can do
in such a case is to take a look at the file `*_progress.txt`, where `*`
stands for the simulation name (given to the `Simulation` class when creating
the simulation oject). For example, if you created your simulation object with
a line such as

    
    
    s = nmag.Simulation('one')
    

Then you may be looking for a file with name `one_progress.txt`. If you used
simply `s = nmag.Simulation()` and your file is named `two.py` then you should
look for a file with name `two_progress.txt`. This file contains statistics
about the time integrator. You'll first get the current time, step number,
etc. Then you'll get a list of rows each containing four columns, such as

    
    
    123 0.456 0.123 None
    

Column 1 is the step reached, an integer number which always increases. The
file shows convergence statistics for the last few steps (it doesn't contain
statistics for all the steps, since this would make it quickly very big).
Column 2 contains the current value of max || dM/dt ||. Column 3 contains the
stopping value of dM/dt. Convergence is reached when column 2 < column 3 for
at least two times. If the simulations is going well, then you should see that
column 2 contains numbers which are not oscillating rapidly and are rather
decreasing or increasing "smoothly". This is what typically should happen,
even if it can be that your simulation has really a bizarre dynamics which
really oscillates in a frenetic way, so one should be careful when analysing
the data. The fourth column contains an evaluation of the quality of the
convergence according to what we just said. This number should be close to one
when the convergence is smooth and close to zero when it is oscillating
frenetically.

# What to do in case of convergence problems¶

If your simulation has really a convergence problem, you can do two things:

  1. improve the tolerances `ts_abs_err` and `ts_rel_err` (decrease these numbers) by using the method `set_params` of the `Simulation` object;
  2. use a `do=[('next_stage', at('stage_time', SI(x, 's')))]` as an argument to the `hysteresis` method. This way you impose a maximum time `x` to spend in the computation of a stage (you should make sure this makes sense in your case).

* * *

# Compiling on Mac OS X Snow Leopard¶

## Updating the OCaml compiler, GSL and OCamlGSL¶

Compilation of Nmag on Mac OS X Snow Leopard requires to update the OCaml
compiler to the latest version.

Indeed, some users reported problems with OCaml compiler 3.09.3, which does
not seem to support the newest OS/architecture.

One thing you could try is to update to the latest version of OCaml. You'll
see that this will require - in turn - to update to the latest versions of GSL
and OCamlGSL. Here I explain how to do that.

Firstly, you should untar again Nmag to get a fresh copy of the nmag all-
source directory.

    
    
    tar xzvf nmag-0.1-all.tar.gz
    

Then you should enter the newly created directory (named simply nmag-0.1) and
get the latest versions of the three packages:

    
    
    cd nmag-0.1
    cd pkgs
    wget http://caml.inria.fr/pub/distrib/ocaml-3.11/ocaml-3.11.1.tar.bz2
    wget ftp://www.mirrorservice.org/sites/ftp.gnu.org/gnu/gsl/gsl-1.14.tar.gz
    wget http://oandrieu.nerim.net/ocaml/gsl/ocamlgsl-0.6.0.tar.gz
    cd ..
    

Now edit the file nmag-0.1/Makefile with your favourite editor.

Search for the string "ocaml-3.09.3", you'll find just one occurrence. Change
it to "ocaml-3.11.1".

Do the same for the other two strings "gsl-1.8.tar.gz" and
"ocamlgsl-0.4.0.tar.gz". Replace them with "gsl-1.14.tar.gz" and
"ocamlgsl-0.6.0.tar.gz", respectively.

## Patching Nmag to work with OCaml 3.11¶

The new version of the OCaml compiler introduces some incompatibilities in the
camlp4 preprocessor (which is bad, I think, and is the reason why OCamlGSL
didn't work anymore) and some incompatibilites in the implementation, which is
acceptable, but breaks one small piece of our code.

The solution is the following. Download the file objsize.c using on the
following link [http://dl.dropbox.com/u/1820549/objsize.c](http://dl.dropbox.c
om/u/1820549/objsize.c)

I now assume you downloaded it in your home directory. Then:

    
    
    cd nmag-0.1 # we go into the directory where nmag was unpacked
    cd nsim/snippets
    mv objsize.c old-objsize.c
    mv ~/objsize.c .
    

As you see you are basically replacing the file
nmag-0.1/nsim/snippets/objsize.c with the one you just downloaded before.

## Patching Petsc¶

There are some more steps to do in order to get Nmag working on your Mac Snow
Leopard:

    
    
    cd nmag-0.1 # you should get inside the directory nmag-0.1
    make .deps_petsc_patch
    

Your system will now spend some minutes compiling some libraries.

When it finishes you should do as follows:

    
    
    cd lib/petsc/bmake/common
    mv rules.shared.basic old-rules.shared.basic
    wget http://dl.dropbox.com/u/1820549/rules.shared.basic
    

This line will replace the file `bmake/common/rules.shared.basic` in the Petsc
distribution.

After this you should be able to finally compile Nmag:

    
    
    make
    

* * *

# User contributed content¶

## Recipes, useful info¶

Using Salome as a CAD tool for creating complex meshes

Script to import .unv mesh from Salome platform

Example of user provided content

Performance data - memory usage, runtimes for particular simulations

Probing the magnetization along a curve

Script to calculate multipole expansion of magnetic charge

Scripts to create meshes for granular media

## Installation issues¶

How to install Nmag 0.1 beta (6481) on Fedora 14 (64 bit)

* * *

# Example of user provided content¶

To add your own content go back to the previous page and click the link `edit`
which you can find on the right at the top of the text editing box.

To add a page that, for example, might provide a recipe how to achieve X, you
would add a line

` [`[How to achieve X]]

Try to choose a good title here as it will become part of the URL for the Wiki
page you are about to create.

You can use the `Preview` link to check what this will look like. You should
expect that your new line (`How to achieve X`) shows in red colour -- this is
a sign that (i) it is a link but (ii) the link is pointing to a Wikipage that
does not yet exist.

Once you are happy with this, add a comment in the comment box (for example
`Adding link to "How to achieve X"`) and press the `Save` button. Providing
comments will be useful if we need to go back through the history of the
webpage (in case somebody has broken something accidentally).

Your new line will be rendered in the user contribution page as

How to achieve X

You can now click on this link a new page will open. This is your own Wiki
page, you can add content inside it.

You can find more help (while you are in edit mode) on how to edit Wiki pages
by clicking the `Help` link (just over the text edit box on the right). Note
that at the bottom of the help windows there is another link to even more
detailed formatting.

* * *

# Using Gmsh¶

If you want to create many meshes using Gmsh, you may first generate a mesh
manually.

Then you can create a Python script which uses this mesh as a template to
quickly create a mesh for a different set of parameters.

Here is a script which shows how to do so. The mesh file (geo) has been
enclosed between quotes `"""` and some of the values for the points
coordinates have been substituted with strings that the Python script
substitutes with real values.

Note that we use `Mesh.CharacteristicLengthFactor = 5.0;` to control the
discretisation of the mesh. We also use `Physical Volume(1) = {1};` to make
sure that the mesh region is labeled starting from region number 1.

    
    
    mesh = """ 
    cl1 = 1;
    Point(1) = {$x2$, 0, 0, cl1};
    Point(2) = {$x2$, $x2$, 0, cl1};
    Point(3) = {0, $x2$, 0, cl1};
    Point(4) = {0, $x1$, 0, cl1};
    Point(5) = {$x1$, 0, 0, cl1};
    Point(6) = {$x0$, $x0$, 0, cl1};
    Point(7) = {$x0$, $x1$, 0, cl1};
    Point(8) = {$x1$, $x0$, 0, cl1};
    Point(9) = {$x2$, 0, $y1$, cl1};
    Point(10) = {$x1$, 0, $y1$, cl1};
    Point(14) = {$x1$, $x0$, $y1$, cl1};
    Point(18) = {$x0$, $x0$, $y1$, cl1};
    Point(19) = {$x0$, $x1$, $y1$, cl1};
    Point(23) = {0, $x1$, $y1$, cl1};
    Point(27) = {0, $x2$, $y1$, cl1};
    Point(31) = {$x2$, $x2$, $y1$, cl1};
    Line(1) = {1, 5};
    Line(2) = {5, 8};
    Circle(3) = {8, 6, 7};
    Line(4) = {7, 4};
    Line(5) = {4, 3};
    Line(6) = {3, 2};
    Line(7) = {2, 1};
    Line(11) = {9, 10};
    Line(12) = {10, 14};
    Circle(13) = {14, 18, 19};
    Line(14) = {19, 23};
    Line(15) = {23, 27};
    Line(16) = {27, 31};
    Line(17) = {31, 9};
    Line(19) = {1, 9};
    Line(20) = {5, 10};
    Line(24) = {8, 14};
    Line(28) = {7, 19};
    Line(32) = {4, 23};
    Line(36) = {3, 27};
    Line(40) = {2, 31};
    Line Loop(9) = {1, 2, 3, 4, 5, 6, 7};
    Plane Surface(9) = {9};
    Line Loop(21) = {1, 20, -11, -19};
    Ruled Surface(21) = {21};
    Line Loop(25) = {2, 24, -12, -20};
    Ruled Surface(25) = {25};
    Line Loop(29) = {3, 28, -13, -24};
    Ruled Surface(29) = {29};
    Line Loop(33) = {4, 32, -14, -28};
    Ruled Surface(33) = {33};
    Line Loop(37) = {5, 36, -15, -32};
    Ruled Surface(37) = {37};
    Line Loop(41) = {6, 40, -16, -36};
    Ruled Surface(41) = {41};
    Line Loop(45) = {7, 19, -17, -40};
    Ruled Surface(45) = {45};
    Line Loop(46) = {11, 12, 13, 14, 15, 16, 17};
    Plane Surface(46) = {46};
    Surface Loop(1) = {9, 46, 21, 25, 29, 33, 37, 41, 45};
    
    Volume(1) = {1};
    
    Physical Volume(1) = {1};
    
    Mesh.CharacteristicLengthFactor = $discret$;
    """ 
    
    def create_mesh(filename,
                    inner_size=100.0,
                    curvature=5.0,
                    width=10.0,
                    thickness=20.0,
                    discretisation=2.5):
      global mesh
      s = str(mesh)
      x = 0.5*inner_size
      variables = [("x0", x - curvature),
                   ("x1", x),
                   ("x2", x + 0.5*width),
                   ("y1", thickness),
                   ("discret", discretisation)]
      for variable_name, variable_value in variables:
        s = s.replace("$%s$" % variable_name, str(variable_value))
    
      f = open(filename, "w")
      f.write(s)
      f.close()
    
    create_mesh("dots.geo")
    

* * *

# How to visualise the difference between two fields defined over the same
mesh?¶

First save the data into two **ASCII** VTK files. For example,

    
    
    nmagpp --vtk=m.vtk --vtkascii --fields=m simulation_name
    

Note the option `"--vtkascii"` to force the creation of a ASCII file.

Let's say this command created the two files `m-000000.vtk` and
`m-000001.vtk`.

You can now use the library `pyvtk` to load the two files, compute the
difference and save it back to a third file.

    
    
    import numpy, pyvtk
    a = pyvtk.VtkData("m-000000.vtk")
    b = pyvtk.VtkData("m-000001.vtk")
    va = a.point_data.data[0].vectors
    vb = b.point_data.data[0].vectors
    for i in range(len(va)):
        va[i] = list(numpy.array(va[i]) - numpy.array(vb[i]))
    a.tofile("difference.vtk")
    

Save this text to a file named `diff.py` and run it as:

    
    
    python diff.py
    

You'll get a third file with name `difference.vtk` containing the difference
of the two fields.

## A step forward¶

If you are repeating this operation many times, it may become annoying to open
again and again the `diff.py` file to change the names of the input files. You
can then modify the script as follows:

    
    
    import sys, numpy, pyvtk
    a = pyvtk.VtkData(sys.argv[1])
    b = pyvtk.VtkData(sys.argv[2])
    va = a.point_data.data[0].vectors
    vb = b.point_data.data[0].vectors
    for i in range(len(va)):
        assert a.structure.points[i] == b.structure.points[i]
        va[i] = list(numpy.array(va[i]) - numpy.array(vb[i]))
    a.tofile(sys.argv[3])
    

The name of the files are taken from the command line. You can then compute
the difference using:

    
    
    python diff.py a.vtk b.vtk a_minus_b.vtk 
    

Notice that in the last version of the script we also added the line,

    
    
    assert a.structure.points[i] == b.structure.points[i]
    

which does just check that the two files are using the same set of points
(i.e. the same mesh).
