CFLAGS := -DHB_TINY

ifdef VSCMD_VER
	PLATFORM := MSVC
else
	PLATFORM := UNIX
endif

ifeq ($(PLATFORM),MSVC)
	# Default compiler options for Microsoft Visual C++ (MSVC)
	CC	:= cl
	CXX	:= cl
	OBJEXT	:= dll
	RM	:= del
	CFLAGS	+= /nologo /utf-8 /W1 /FS /D_CRT_SECURE_NO_WARNINGS /MT /O2 /GL /LD /DHB_DLL_EXPORT

else
	CC	:= cc
	CXX	:= c++
	OBJEXT	:= so
	RM	:= rm -f
	CFLAGS	+= -O2 -shared -g1

endif

harfbuzz.$(OBJEXT): harfbuzz.cc
	$(CXX) $(CFLAGS) -o $@ $^

%.dll: %.cc
	$(CXX) $(CFLAGS) /Fe$@ $^
