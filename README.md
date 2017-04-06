CLASS: Cosmic Linear Anisotropy Solving System  {#mainpage}
==============================================

Authors: Julien Lesgourgues and Thomas Tram

with several major inputs from other people, especially Benjamin
Audren, Simon Prunet, Jesus Torrado, Miguel Zumalacarregui, Francesco
Montanari, etc.

For download and information, see http://class-code.net

CLASS.FreeSF: Cosmic Linear Anisotropy Solving System for a free scalar field
==============================================

Amendment made by: L. Arturo Urena-Lopez

with help from Alma X. Gonzalez-Morales and Francisco X. Linares Cedeño.

For download see: https://github.com/lurena-lopez/class.FreeSF

This particular version of the CLASS code was amended to solve the case of a free scalar field as a dark matter component (dubbed as ScalarFieldDarkMater, or SFDM for short), endowed with a potential (1/2) m^2 phi^2, and using the formalism developed in the paper 'Towards accurate cosmological predictions for rapidly oscillating scalar fields as dark matter', by L. Arturo Ureña-López and Alma X. Gonzalez-Morales, published in JCAP 1607 (2016) no.07, 048. See also https://arxiv.org/abs/1511.08195.

CLASS.FreeSF works as usual for CDM only, or for SFDM only, but also for a mixture of the two. Also, CLASS.FreeSF works seamlessly with all other tools made for and used by the original CLASS code.

The set up of scalar field quantities follows closely the instructions of CLASS for scalar fields, see item 8) in the file explanatory.ini. In particular, to have a run with SFDM proceed as indicated below.
    1. Omega_cdm must be specified in item 5). 
        1a. Set Omega_cdm = 1.e-4 or smaller if a run is needed with SFDM as the only dark matter component. Beware that CLASS requires a non-zero value of Omega_cdm to correctly define the synchronous gauge of metric perturbations.
        1b. Otherwise set Omega_cdm to your preferred value, and the SFDM budget will be calcualted internally (see below).
    2. In item 8a):
        2a. Omega_Lambda must be specified.
        2b. Omega_fld must be specified.
        2c. Omega_scf must be set to a negative value, and CLASS will calculate it internally from the fulfillment of the Friedmann constraint.
    3. The scalar field parameters are given as entries in the row vector scf_parameters[] in item 8d). Here is a description of their meaning.
        3a. scf_parameters[0]= 0. by default.
        3b. scf_parameters[1]= boson mass in units of eV.
        3c. scf_parameters[2]= initial value of the potential variable y1. The default value is the attractor solution, which is calculated internally. To modify this default behavior you must change item 8c) and then set scf_parameters[2] to your preferred initial value (do this under your own responsibility!).
        3d. scf_parameters[2]= 1.e-2 is the default value of the tuning parameter, see also item 8e). This default value has been tested for an ample range of boson masses, but it can be changed if necessary.
For concrete examples, see the file lcdm.ini for a run with the standard cold dark matter model, and the file lsfdm.ini for a run with the scalar field fulfilling the dark matter budget. See the CLASS documentation for information to change other cosmological parameters.

You can use CLASS.FreeSF freely, provided that in your publications you cite the paper 'Towards accurate cosmological predictions for rapidly oscillating scalar fields as dark matter', JCAP 1607 (2016) no.07, 048, https://arxiv.org/abs/1511.08195

Below is the original CLASS documentation, that you must follow for instructions about installation and compilation of the code.

==============================================

Compiling CLASS and getting started
-----------------------------------

(the information below can also be found on the webpage, just below
the download button)

After downloading the code, unpack the archive (tar -zxvf
class_v*.tar.gz), go to the class directory (cd class_v*/) and compile
(make clean; make class). If the first compilation attempt fails, you
may need to open the Makefile and adapt the name of the compiler
(default: gcc), of the optimization flag (default: -O4) and of the
OpenMP flag (default: -fopenmp; this flag is facultative, you are free
to compile without OpenMP if you don't want parallel execution; note
that you need the version 4.2 or higher of gcc to be able to compile
with -fopenmp). Several details on the CLASS compilation are given on
the wiki page

https://github.com/lesgourg/class_public/wiki/Installation

(in particular, for compiling on Mac 10.9 Mavericks).

To check that the code runs, type:

    ./class explanatory.ini

The explanatory.ini file is a reference input file, containing and
explaining the use of all possible input parameters. We recommend to
read it, to keep it unchanged (for future reference), and to create
for your own purposes some shorter input files, containing only the
input lines which are useful for you. Input files must have a *.ini
extension.

If you want to play with the precision/speed of the code, you can use
one of the provided precision files (e.g. cl_permille.pre) or modify
one of them, and run with two input files, for instance:

    ./class test.ini cl_permille.pre

The automatically-generated documentation is located in

    doc/manual/html/index.html
    doc/manual/CLASS_manual.pdf

On top of that, if you wish to modify the code, you will find lots of
comments directly in the files.

Python
------

To use CLASS from python, or ipython notebooks, or from the Monte
Python parameter extraction code, you need to compile not only the
code, but also its python wrapper. This can be done by typing just
'make' instead of 'make class'. More details on the wrapper and its
compilation are found on the wiki page

https://github.com/lesgourg/class_public/wiki

Plotting utility
----------------

Since version 2.3, the package includes an improved plotting script
called CPU.py (Class Plotting Utility), written by Benjamin Audren and
Jesus Torrado. It can plot the Cl's, the P(k) or any other CLASS
output, for one or several models, as well as their ratio or percentage
difference. The syntax and list of available options is obtained by
typing 'pyhton CPU.py --help'. There is a similar script for MATLAB,
written by Thomas Tram. To use it, once in MATLAB, type 'help
plot_CLASS_output.m'

Developing the code
--------------------

If you want to develop the code, we suggest that you download it from
the github webpage

https://github.com/lesgourg/class_public

rather than from class-code.net. Then you will enjoy all the feature
of git repositories. You can even develop your own branch and get it
merged to the public distribution. For related instructions, check

https://github.com/lesgourg/class_public/wiki/Public-Contributing

Using the code
--------------

You can use CLASS freely, provided that in your publications, you cite
at least the paper `CLASS II: Approximation schemes <http://arxiv.org/abs/1104.2933>`_. Feel free to cite more CLASS papers!

Support
-------

To get support, please open a new issue on the

https://github.com/lesgourg/class_public

webpage!
