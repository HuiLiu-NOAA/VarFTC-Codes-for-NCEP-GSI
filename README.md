# VarFTC-Codes-for-NCEP-GSI
Brief description of the VarFTC implementation in NOAA/NCEP Global_workflow v15.3

This prototype VarFTC implementation in the GSI is based on Hoffman et al (2022). The VarFTC operator calculates an optimal weighted average (plus a constant term) over a vertical pressure grid (layer) with a variable depth of up to a few hundreds hPa. The usual calculation of the background AMV is applied/repeated at multiple levels within the layer. The original GSI codes are modifdied to accormodate VarFTC forward, tangent linear and adjoint codes. The VarFTC is applied to all AMV types assimilated in GSI.

In this implementation, the VarFTC coefficients used in the forward calculation are calculated offline. The setupw.f90 is modified to output GFS background wind profile at each AMV location. The GSI analysis script is modified to activate/call the offline R-based calculation package (developed by Ross N. Hoffman), which calculates the optimal vertical averaging depth, vertical offset around AMV height, and weights for the averaging. The GFS and AMV outputs over the previous 24 DA cycles are used in the calculation. A minimum of 1000 AMVs for each AMV type in the high (100-450 hPa), middle (450-800 hPa), and low layer (800-1000 hPa) of the Southern Hemisphere, Tropics, or Northern Hemisphere is required in the calculation. 
The resulting VarFTC averaging weights are read in and applied to the original error specification for AMVs in the read_satwind.f90. 

It is shown that the VarFTC operator reduces the RMSD of OmB (by up to 10% varying on AMV types) compared to the operational operator. The RMSD ratio of the OmB (VarFTC/OPER) are used as the weights to scale the prescribed errors of AMVs in GSI. 


Contributors: Ross N. Hoffman, Hui Liu, Kayo Ide, Kevin Garrett, Katherine Lukens

The code archive locations:

https://github.com/HuiLiu-NOAA/VarFTC-Codes-for-NCEP-GSI

VarFTC related codes:

read_satwnd.f90:
read in the RMSD ratio of OmB (VarFTC/OPER) calculated by the VarFTC and operational operator.

setupw.f90:
Add the forward operator of VarFTC and calculate OmB of AMV winds using the VarFTC operator. The GFS background winds at AMV locations are outputed for the offline VarFTC calculation.

gridmod.f90, intpw.f90, stpw.f90, m_wNode.F90:
Add the tangent linear and adjoint codes for the VarFTC operator.


----- Reference and how to cite these codes ----

Hoffman et al. 2022, QJRMS, doi: 10.1002/qj.4207

Hoffman R.-N., H. Liu, K. Garrett, K. Ide, and K. Lukens, 2023: Assimilating Atmospheric Motion Vector (AMV) Winds Using a Variational Feature Track Correction (VarFTC) (in preparation).
