# VarFTC-Codes-for-NCEP-GSI
Brief description of the VarFTC codes in NOAA/NCEP Global_workflow v15.3:

The VarFTC implementation in the GSI is based on Hoffman et al (2022). The original GSI related codes are modifdied to accormodate VarFTC.

Specifically, The VarFTC forward, tangent linear and adjoint codes are added into the GSI codes. The observation error specified to AMV winds are tuned donw according to the STDV reduction of OmB RMSD by VarFTC. The VarFTC is applied to all AMV types.

Contributors: Ross N. Hoffman, Hui Liu, Kayo Ide, Kevin Garrett, Katherine Lukens

Archive locations:

https://github.com/HuiLiu-NOAA/VarFTC-Codes-for-NCEP-GSI

VarFTC related codes:

read_satwnd.f90:
read in the reduction ratio of OmB RMSD by VarFTC.

setupw.f90:
process Add the forward operator of VarFTC and calculate OmB of AMV winds using the VarFTC operator.

gridmod.f90, intpw.f90, stpw.f90, m_wNode.F90:
Add the tangent linear and adjoint codes for the VarFTC operator.

----- How to cite these codes ----

Hoffman et al. 2022, QJRMS, doi: 10.1002/qj.4207

Hoffman R.-N., H. Liu, K. Garrett, K. Ide, and K. Lukens, 2023: Assimilating Atmospheric Motion Vector (AMV) Winds Using a Variational Feature Track Correction (VarFTC) (in preparation).
