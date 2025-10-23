FFC = mpinfort -compiler /opt/nec/ve/nfort/5.3.0/bin/nfort

FFLAGS  = -report-all -O3 -fpp $(EXTRA) #-mparallel
FFLAGS  += -fdiag-vector=2 -fdiag-inline=2 -fdiag-parallel=2

NLC_HOME=/opt/nec/ve/nlc/3.1.0
INC = -I$(NLC_HOME)/include
LIB = -L$(NLC_HOME)/lib  -laslfftw3 -lasl_sequential 
LIB += -L$(NLC_HOME)/lib  -laslfftw3 -lasl_sequential -ftrace
LIB += -L/opt/nec/ve/nfort/5.3.0/lib -lnfort

SRC = ../src/
MYL = ../src/
CWD = ./
OUT = rmhdfs.exe

MATH = rmhdfs_r1.0_math
MATRIX = LB_m2.1_matrix

rmhdfs:	$(SRC)rmhdfs_r1.0_header.f90\
	$(SRC)rmhdfs_r1.0_mpienv.f90\
	$(MYL)$(MATH).f90\
	$(MYL)$(MATRIX).f90\
	$(SRC)rmhdfs_r1.0_clock.f90\
	$(SRC)rmhdfs_r1.0_intgrl.f90\
	$(SRC)rmhdfs_r1.0_bndry.f90\
	$(SRC)rmhdfs_r1.0_pssn_fftw.f90\
	$(SRC)rmhdfs_r1.0_fld.f90\
	$(SRC)rmhdfs_r1.0_feedback.f90\
	$(SRC)rmhdfs_r1.0_diag.f90\
	$(SRC)rmhdfs_r1.0_set.f90\
	$(SRC)rmhdfs_r1.0_advnc.f90\
	$(SRC)rmhdfs_r1.0_main.f90
	
	$(FFC) $(FFLAGS) -c $(SRC)rmhdfs_r1.0_header.f90
	$(FFC) $(FFLAGS) -c $(SRC)rmhdfs_r1.0_mpienv.f90
	$(FFC) $(FFLAGS) -c $(MYL)$(MATH).f90 $(INC)
	$(FFC) $(FFLAGS) -c $(MYL)$(MATRIX).f90
	$(FFC) $(FFLAGS) -c $(SRC)rmhdfs_r1.0_clock.f90
	$(FFC) $(FFLAGS) -c $(SRC)rmhdfs_r1.0_intgrl.f90
	$(FFC) $(FFLAGS) -c $(SRC)rmhdfs_r1.0_bndry.f90
	$(FFC) $(FFLAGS) -c $(SRC)rmhdfs_r1.0_pssn_fftw.f90 $(INC)
	$(FFC) $(FFLAGS) -c $(SRC)rmhdfs_r1.0_fld.f90
	$(FFC) $(FFLAGS) -c $(SRC)rmhdfs_r1.0_feedback.f90
	$(FFC) $(FFLAGS) -c $(SRC)rmhdfs_r1.0_diag.f90
	$(FFC) $(FFLAGS) -c $(SRC)rmhdfs_r1.0_set.f90
	$(FFC) $(FFLAGS) -c $(SRC)rmhdfs_r1.0_advnc.f90
	$(FFC) $(FFLAGS) -c $(SRC)rmhdfs_r1.0_main.f90
	
	$(FFC) $(FFLAGS) rmhdfs_r1.0_main.o\
			rmhdfs_r1.0_header.o\
			rmhdfs_r1.0_mpienv.o\
			$(MATH).o\
			$(MATRIX).o\
			rmhdfs_r1.0_clock.o\
			rmhdfs_r1.0_intgrl.o\
			rmhdfs_r1.0_bndry.o\
			rmhdfs_r1.0_fld.o\
			rmhdfs_r1.0_feedback.o\
			rmhdfs_r1.0_diag.o\
			rmhdfs_r1.0_set.o\
			rmhdfs_r1.0_pssn_fftw.o\
			rmhdfs_r1.0_advnc.o\
			-o $(OUT) $(LIB)

clean:
	rm -f ./*.o ./*.mod ./*.lst ./*.exe ./*.err ./*.out ./*.L ./sub.q.00* ./rmhdfs_r1.0.nml.*

clear:
	rm -f ./*.o ./*.mod ./*.lst ./*.err ./*.out
