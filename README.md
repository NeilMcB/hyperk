# hyperk
Repository for analysis code edited during the LAPPD test summer project
------------------------------------------------------------------------

pickle_data_lcwp.py:
------------------------------------------------------------------------
Converts .txt files containing the hexadecimal representation of  LeCroy 
WavePro 950 oscilloscope traces and converts them to .pkl files for use 
in make_spectra.py
Run as: python pickle_data_lcwp.py <directory> <channel>
The conversion parameters can be obtained from the LabView "Instrument 
Parameters" output.
Returns two files for input to make_spectra.py

Potential improvements:
------------------------------------------------------------------------
An input file containing information on the 'scope parameters would save 
some time and perhaps reduce the chance of error - this could be produced 
using LabView. 
Automation through an entire directory of different measurements - e.g. 
various HV values when taking a gain curve - is simple to implement. 
See some of the TekTronix pickle codes for an example.
It should be possible to read n_samples automatically - either from the 
LabView parameter file, or from the input file directly.

pickle_data_lcwp_dir.py:
------------------------------------------------------------------------
Does the same as above, but the <directory> argument concerns a folder
containing an entire set of measurments which can be processed at once.

make_spectra.py:
------------------------------------------------------------------------
Calculates the gain and returns plots showing the maximum voltages vs 
time, the charge spectrum, the signal amplitude spectrum and a series of 
oscilloscope traces.
Run as: python make_spectra.py <directory> <channel>
The gain will be printed to terminal.
Often the script will fail when it tries to plot the sample traces for weaker
signals. This is becuase it can't find enough to take a sample of four from.
This can be solved by changing the limits of subset1, subset2 and subset3. 