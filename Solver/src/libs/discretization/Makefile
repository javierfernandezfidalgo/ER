#################################################
#	Spectral Makefile 		#
#################################################
INSTALL_DIR?=./
FFLAGS?=-cpp
AR?=ar
ARFLAGS?=cr
RANLIB?=ranlib
MOD_FLAG?=-J

LIBOBJS_NS =    ./build_ns/DGSEMClass.o \
		./build_ns/DGIntegrals.o \
		./build_ns/GradientsStabilization.o \
                ./build_ns/RegionsDetectionKeywords.o \
		./build_ns/ERSensor.o \
		./build_ns/VisSensorClass.o \
		./build_ns/VisRegionsDetection.o \
		./build_ns/HyperbolicDiscretizationClass.o \
		./build_ns/HyperbolicStandard.o \
		./build_ns/HyperbolicSplitForm.o \
		./build_ns/HyperbolicDiscretizations.o \
		./build_ns/EllipticDiscretizationClass.o \
		./build_ns/EllipticIP.o \
		./build_ns/EllipticBR1.o \
		./build_ns/EllipticBR2.o \
		./build_ns/EllipticDiscretizations.o \
		./build_ns/WallFunctionConnectivity.o \
		./build_ns/ShockCapturingKeywords.o \
		./build_ns/SVV.o \
		./build_ns/SCsensorClass.o \
		./build_ns/ShockCapturing.o \


LIBOBJS_NSSA =  ./build_nssa/DGSEMClass.o \
		./build_nssa/DGIntegrals.o \
		./build_nssa/GradientsStabilization.o \
		./build_nssa/RegionsDetectionKeywords.o \
		./build_nssa/ERSensor.o \
		./build_nssa/VisSensorClass.o \
		./build_nssa/VisRegionsDetection.o \
		./build_nssa/HyperbolicDiscretizationClass.o \
		./build_nssa/HyperbolicStandard.o \
		./build_nssa/HyperbolicSplitForm.o \
		./build_nssa/HyperbolicDiscretizations.o \
		./build_nssa/EllipticDiscretizationClass.o \
		./build_nssa/EllipticIP.o \
		./build_nssa/EllipticBR1.o \
		./build_nssa/EllipticBR2.o \
		./build_nssa/EllipticDiscretizations.o \
		./build_nssa/WallFunctionConnectivity.o \
		./build_nssa/ShockCapturingKeywords.o \
		./build_nssa/SVV.o \
		./build_nssa/SCsensorClass.o \
		./build_nssa/ShockCapturing.o \

LIBOBJS_iNS =   ./build_ins/DGSEMClass.o \
		./build_ins/DGIntegrals.o \
		./build_ins/GradientsStabilization.o \
		./build_ins/HyperbolicDiscretizationClass.o \
		./build_ins/HyperbolicStandard.o \
		./build_ins/HyperbolicSplitForm.o \
		./build_ins/HyperbolicDiscretizations.o \
		./build_ins/EllipticDiscretizationClass.o \
		./build_ins/EllipticIP.o \
		./build_ins/EllipticBR1.o \
		./build_ins/EllipticBR2.o \
		./build_ins/EllipticDiscretizations.o \

LIBOBJS_CH =    ./build_ch/DGSEMClass.o \
		./build_ch/DGIntegrals.o \
		./build_ch/GradientsStabilization.o \
		./build_ch/HyperbolicDiscretizationClass.o \
		./build_ch/HyperbolicStandard.o \
		./build_ch/HyperbolicSplitForm.o \
		./build_ch/HyperbolicDiscretizations.o \
		./build_ch/EllipticDiscretizationClass.o \
		./build_ch/EllipticIP.o \
		./build_ch/EllipticBR1.o \
		./build_ch/EllipticBR2.o \
		./build_ch/EllipticDiscretizations.o

LIBOBJS_MU =  ./build_mu/DGSEMClass.o \
		./build_mu/DGIntegrals.o \
		./build_mu/GradientsStabilization.o \
		./build_mu/HyperbolicDiscretizationClass.o \
		./build_mu/HyperbolicStandard.o \
		./build_mu/HyperbolicDiscretizations.o \
		./build_mu/EllipticDiscretizationClass.o \
		./build_mu/EllipticIP.o \
		./build_mu/EllipticBR1.o \
		./build_mu/EllipticBR2.o \
		./build_mu/EllipticDiscretizations.o

LIB = discretization

############################################
#	MAIN COMPILATION RULES 		   #
############################################
.DEFAULT_GOAL:=all

all: lib$(LIB)_ns.a lib$(LIB)_nssa.a lib$(LIB)_ins.a lib$(LIB)_ch.a lib$(LIB)_mu.a

./build_ns/%.o: %.f90
	@echo
	@echo $<
	$(FC) $(FFLAGS) -DNAVIERSTOKES -I./include_ns $(MACROS) $(EXTLIB_INC) $(INCLUDE) $(INCLUDE)_ns -c $< -o $@ $(MOD_FLAG) ./include_ns

./build_nssa/%.o: %.f90
	@echo
	@echo $<
	$(FC) $(FFLAGS) -DNAVIERSTOKES -DSPALARTALMARAS -I./include_nssa $(MACROS) $(EXTLIB_INC) $(INCLUDE) $(INCLUDE)_nssa -c $< -o $@ $(MOD_FLAG) ./include_nssa

./build_ins/%.o: %.f90
	@echo
	@echo $<
	$(FC) $(FFLAGS) -DINCNS -I./include_ins $(MACROS) $(EXTLIB_INC) $(INCLUDE) $(INCLUDE)_ins -c $< -o $@ $(MOD_FLAG) ./include_ins

./build_ch/%.o: %.f90
	@echo
	@echo $<
	$(FC) $(FFLAGS) -DCAHNHILLIARD -I./include_ch $(MACROS) $(EXTLIB_INC) $(INCLUDE) $(INCLUDE)_ch -c $< -o $@ $(MOD_FLAG) ./include_ch

./build_mu/%.o: %.f90
	@echo
	@echo $<
	$(FC) $(FFLAGS) -DMULTIPHASE -DCAHNHILLIARD -I./include_mu $(MACROS) $(EXTLIB_INC) $(INCLUDE) $(INCLUDE)_mu -c $< -o $@ $(MOD_FLAG) ./include_mu

lib$(LIB)_ns.a: header mkdirs $(LIBOBJS_NS)
	@echo
	@echo "---------------------------------"
	@echo "| Linking library" $@ "|"
	@echo "---------------------------------"
	@$(RM) $@
	$(AR) $(ARFLAGS) $@ $(LIBOBJS_NS)
	@$(RANLIB) $@

lib$(LIB)_nssa.a: header mkdirs $(LIBOBJS_NSSA)
	@echo
	@echo "---------------------------------"
	@echo "| Linking library" $@ "|"
	@echo "---------------------------------"
	@$(RM) $@
	$(AR) $(ARFLAGS) $@ $(LIBOBJS_NSSA)
	@$(RANLIB) $@

lib$(LIB)_ins.a: header mkdirs $(LIBOBJS_iNS)
	@echo
	@echo "---------------------------------"
	@echo "| Linking library" $@ "|"
	@echo "---------------------------------"
	@$(RM) $@
	$(AR) $(ARFLAGS) $@ $(LIBOBJS_iNS)
	@$(RANLIB) $@

lib$(LIB)_ch.a: header mkdirs $(LIBOBJS_CH)
	@echo
	@echo "---------------------------------"
	@echo "| Linking library" $@ "|"
	@echo "---------------------------------"
	@$(RM) $@
	$(AR) $(ARFLAGS) $@ $(LIBOBJS_CH)
	@$(RANLIB) $@

lib$(LIB)_mu.a: header mkdirs $(LIBOBJS_MU)
	@echo
	@echo "---------------------------------"
	@echo "| Linking library" $@ "|"
	@echo "---------------------------------"
	@$(RM) $@
	$(AR) $(ARFLAGS) $@ $(LIBOBJS_MU)
	@$(RANLIB) $@

install: all
	cp -p lib$(LIB)_ns.a $(INSTALL_DIR)/lib/
	cp -p lib$(LIB)_nssa.a $(INSTALL_DIR)/lib/
	cp -p lib$(LIB)_ins.a $(INSTALL_DIR)/lib/
	cp -p lib$(LIB)_ch.a $(INSTALL_DIR)/lib/
	cp -p lib$(LIB)_mu.a $(INSTALL_DIR)/lib/
	cp -p ./include_ns/*.mod $(INSTALL_DIR)/include_ns/
	cp -p ./include_nssa/*.mod $(INSTALL_DIR)/include_nssa/
	cp -p ./include_ins/*.mod $(INSTALL_DIR)/include_ins/
	cp -p ./include_ch/*.mod $(INSTALL_DIR)/include_ch/
	cp -p ./include_mu/*.mod $(INSTALL_DIR)/include_mu/
	@echo
	@echo

install-mu: lib$(LIB)_mu.a
	cp -p lib$(LIB)_mu.a $(INSTALL_DIR)/lib/
	cp -p ./include_mu/*.mod $(INSTALL_DIR)/include_mu/
	@echo
	@echo

install-ns: lib$(LIB)_ns.a
	cp -p lib$(LIB)_ns.a $(INSTALL_DIR)/lib/
	cp -p ./include_ns/*.mod $(INSTALL_DIR)/include_ns/
	@echo
	@echo

install-nssa: lib$(LIB)_nssa.a
	cp -p lib$(LIB)_nssa.a $(INSTALL_DIR)/lib/
	cp -p ./include_nssa/*.mod $(INSTALL_DIR)/include_nssa/
	@echo
	@echo

header: FORCE
	@echo
	@echo "================================"
	@echo ">>   Building Discretization    "
	@echo "================================"
	@echo
	@echo

mkdirs: FORCE
	@mkdir -p ./include_ns ./include_nssa ./include_ins ./include_ch ./include_mu
	@mkdir -p ./build_ns ./build_nssa ./build_ins ./build_ch ./build_mu

clean: FORCE
	$(RM) lib$(LIB)_ns.a lib$(LIB)_nssa.a lib$(LIB)_ins.a lib$(LIB)_ch.a lib$(LIB)_mu.a
	$(RM) ./build_ns/*.o ./include_ns/*.mod
	$(RM) ./build_nssa/*.o ./include_nssa/*.mod
	$(RM) ./build_ins/*.o ./include_ins/*.mod
	$(RM) ./build_ch/*.o ./include_ch/*.mod
	$(RM) ./build_mu/*.o ./include_mu/*.mod

#############################################
#	Dummy procedure to force a rule     #
#############################################
FORCE:
