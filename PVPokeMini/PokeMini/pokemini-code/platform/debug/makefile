# PokeMini Makefile for GTK + SDL 1.2 (Linux)

POKEROOT = ../../
BUILD = Build
TARGET = PokeMiniD

WINTARGET = PokeMiniD.exe
WINRES_TRG = $(BUILD)/pokemini_rc.o
WINRES_SRC = $(POKEROOT)resource/pokemini.rc

CFLAGS += -Wall `$(SDL_BASE)sdl-config --cflags` `pkg-config --cflags gtk+-2.0` $(INCLUDE)
SLFLAGS += `$(SDL_BASE)sdl-config --libs` `pkg-config --libs gtk+-2.0` -lm -lz

INCDIRS = source sourcex resource freebios dependencies/minizip

OBJS = \
 PokeMini_Debug.o	\
 CPUWindow.o	\
 InputWindow.o	\
 PalEditWindow.o	\
 MemWindow.o	\
 PRCTilesWindow.o	\
 PRCMapWindow.o	\
 PRCSprWindow.o	\
 TimersWindow.o	\
 HardIOWindow.o	\
 IRQWindow.o	\
 MiscWindow.o	\
 SymbWindow.o	\
 TraceWindow.o	\
 ExternalWindow.o	\
 FileAssociation.o	\
 sourcex/KeybMapSDL.o	\
 sourcex/GtkXDialogs.o	\
 sourcex/Font8x12.o	\
 sourcex/PokeMiniIcon_96x128.o	\
 sourcex/InstructionProc.o	\
 sourcex/InstructionInfo.o	\
 sourcex/SGtkXDrawingView.o	\
 sourcex/ExportBMP.o	\
 sourcex/ExportWAV.o	\
 sourcex/HelpSupport.o	\
 freebios/freebios.o	\
 source/PMCommon.o	\
 source/PokeMini.o	\
 source/Multicart.o	\
 Hardware_Debug.o	\
 source/Video.o	\
 source/Video_x1.o	\
 source/Video_x2.o	\
 source/Video_x3.o	\
 source/Video_x4.o	\
 source/Video_x5.o	\
 source/Video_x6.o	\
 source/CommandLine.o	\
 source/MinxCPU.o	\
 source/MinxCPU_XX.o	\
 source/MinxCPU_CE.o	\
 source/MinxCPU_CF.o	\
 source/MinxCPU_SP.o \
 source/MinxTimers.o	\
 source/MinxIO.o	\
 source/MinxIRQ.o	\
 source/MinxPRC.o	\
 source/MinxColorPRC.o	\
 source/MinxLCD.o	\
 source/MinxAudio.o	\
 source/NoUI.o	\
 source/Joystick.o	\
 source/Keyboard.o	\
 dependencies/minizip/unzip.o	\
 dependencies/minizip/ioapi.o	\
 resource/PokeMini_ColorPal.o

DEPENDS_LOCAL = \
 PokeMini_Debug.h	\
 CPUWindow.h	\
 InputWindow.h	\
 PalEditWindow.h	\
 MemWindow.h	\
 PRCTilesWindow.h	\
 PRCMapWindow.h	\
 PRCSprWindow.h	\
 TimersWindow.h	\
 HardIOWindow.h	\
 IRQWindow.h	\
 MiscWindow.h	\
 SymbWindow.h	\
 TraceWindow.h	\
 ExternalWindow.h	\
 FileAssociation.h	\
 Hardware_Debug.h

DEPENDS = \
 freebios/freebios.h	\
 sourcex/KeybMapSDL.h	\
 sourcex/GtkXDialogs.h	\
 sourcex/Font8x12.h	\
 sourcex/PokeMiniIcon_96x128.h	\
 sourcex/InstructionProc.h	\
 sourcex/InstructionInfo.h	\
 sourcex/SGtkXDrawingView.h	\
 sourcex/ExportBMP.h	\
 sourcex/ExportWAV.h	\
 sourcex/HelpSupport.h	\
 source/IOMap.h	\
 source/PMCommon.h	\
 source/PokeMini.h	\
 source/PokeMini_Version.h	\
 source/Multicart.h	\
 source/Video.h	\
 source/Video_x1.h	\
 source/Video_x2.h	\
 source/Video_x3.h	\
 source/Video_x4.h	\
 source/Video_x5.h	\
 source/Video_x6.h	\
 source/CommandLine.h	\
 source/MinxCPU.h	\
 source/MinxTimers.h	\
 source/MinxIO.h	\
 source/MinxIRQ.h	\
 source/MinxPRC.h	\
 source/MinxColorPRC.h	\
 source/MinxLCD.h	\
 source/MinxAudio.h	\
 source/UI.h	\
 source/Joystick.h	\
 dependencies/minizip/unzip.h	\
 dependencies/minizip/ioapi.h	\
 resource/PokeMini_ColorPal.h

BUILDOBJS = $(addprefix $(BUILD)/, $(notdir $(OBJS)))
DEPENDSHDR = $(addprefix $(POKEROOT), $(DEPENDS))
INCLUDE = $(foreach inc, $(INCDIRS), -I$(POKEROOT)$(inc))
VPATH = $(addprefix $(POKEROOT),$(INCDIRS))

.PHONY: all win clean

all: $(BUILD) $(TARGET)

$(BUILD):
	@[ -d @ ] || mkdir -p $@

$(BUILD)/%.o: %.c $(DEPENDSHDR) $(DEPENDS_LOCAL)
	$(CC) $(CFLAGS) -o $@ -c $<

$(TARGET): $(BUILDOBJS)
	$(CC) -o $(TARGET) $(BUILDOBJS) $(SLFLAGS)

win:
	make -f makefile.win

clean:
	-rm -f $(BUILDOBJS) $(TARGET) $(WINTARGET) $(WINRES_TRG)
	-rmdir --ignore-fail-on-non-empty $(BUILD)
