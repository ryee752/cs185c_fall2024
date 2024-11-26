# Issue Summary
The error is caused by a mismatch between the number of processes and the grid parameters. Since these values don't match, the program can't initialize properly and terminates with a fatal error.
# MITgcm Message
The STDERR files indicated that there was a mismatch between the number of processors used and the nPx*nPy
## STDERR0000
(PID.TID 0000.0001) *** ERROR *** EEBOOT_MINIMAL: No. of procs=     2 not equal to nPx*nPy=     1
(PID.TID 0000.0001) *** ERROR *** EEDIE: earlier error in multi-proc/thread setting
(PID.TID 0000.0001) *** ERROR *** PROGRAM MAIN: ends with fatal Error
## STDERR0001
(PID.TID 0001.0001) *** ERROR *** EEBOOT_MINIMAL: No. of procs=     2 not equal to nPx*nPy=     1
(PID.TID 0001.0001) *** ERROR *** EEDIE: earlier error in multi-proc/thread setting
(PID.TID 0001.0001) *** ERROR *** PROGRAM MAIN: ends with fatal Error
# Issue Remedy
I fixed this issue by making sure the number of processors stated in my slurm script matched the grid decomposition parameters by changing the ntasks and np parameters.
