MAIN_SRC=main.cpp romloader.cpp roms.cpp trackloader.cpp utils.cpp video.cpp

#SDL_SRC=sdl/audio.cpp sdl/input.cpp sdl/renderbase.cpp sdl/rendergl.cpp sdl/rendersw.cpp sdl/timer.cpp sdl/renderamiga.cpp

SDL2_SRC=sdl2/audio.cpp sdl2/input.cpp sdl2/renderbase.cpp sdl2/rendergl.cpp sdl2/rendersurface.cpp sdl2/timer.cpp

HWVIDEO_SRC=hwvideo/hwtiles.cpp hwvideo/hwsprites.cpp hwvideo/hwroad.cpp
HWAUDIO_SRC=hwaudio/ym2151.cpp hwaudio/soundchip.cpp hwaudio/segapcm.cpp
FRONTEND_SRC=frontend/ttrial.cpp frontend/menu.cpp frontend/config.cpp frontend/cabdiag.cpp

ENGINE_SRC=engine/outrun.cpp engine/outils.cpp engine/otraffic.cpp engine/otiles.cpp engine/ostats.cpp \
engine/osprites.cpp engine/osprite.cpp engine/osmoke.cpp engine/oroad.cpp engine/opalette.cpp \
engine/ooutputs.cpp engine/omusic.cpp engine/omap.cpp engine/ologo.cpp engine/olevelobjs.cpp \
engine/oinputs.cpp engine/oinitengine.cpp engine/ohud.cpp engine/ohiscore.cpp engine/oferrari.cpp \
engine/ocrash.cpp engine/obonus.cpp engine/oattractai.cpp engine/oanimseq.cpp

ENGINE_AUDIO_SRC=engine/audio/osound.cpp engine/audio/osoundint.cpp
DIRECTX_SRC=directx/ffeedback.cpp
CANNONBOARD=cannonboard/asyncserial.cpp cannonboard/interface.cpp

SRC=$(MAIN_SRC) $(SDL2_SRC) $(HWVIDEO_SRC) $(HWAUDIO_SRC) $(FRONTEND_SRC) $(ENGINE_SRC) \
	$(ENGINE_AUDIO_SRC) $(DIRECTX_SRC) $(CANNONBOARD)

OBJ=$(SRC:.cpp=.o)

INCLUDES=-Isdk:local/newlib/include/SDL2 -Isdl2 -Ihwvideo -Ihwaudio -Ifrontend -Iengine -I. -Icode:ports/boost_1_54_0

DEFINES=-DSDL2

CPPFLAGS=-O2 -ggdb $(INCLUDES) $(DEFINES) #-Wall
LDFLAGS= -lSDL2 -lpthread -use-dynld -ldl -lauto -lunix

NAME=CannonBall

#g++ -o video.o $(CPPFLAGS) -c video.cpp

#normal:
#	make all
#	copy $(NAME) $(NAME)SDL2

all: $(OBJ) #makefile.os4
	g++ -o $(NAME) $(OBJ) $(LDFLAGS) 

#GL: 
#	g++ -o video.o $(CPPFLAGS) $(OPENGL) -c video.cpp
#	make all

%.o: %.cpp
	g++ -o $@ $(CPPFLAGS) -c $<

sdl2/%.o: sdl2/%.cpp
	g++ -o $@ $(CPPFLAGS) -c $<

hwvideo/%.o: hwvideo/%.cpp
	g++ -o $@ $(CPPFLAGS) -c $<

hwaudio/%.o: hwaudio/%.cpp
	g++ -o $@ $(CPPFLAGS) -c $<

frontend/%.o: frontend/%.cpp
	g++ -o $@ $(CPPFLAGS) -c $<

engine/%.o: engine/%.cpp
	g++ -o $@ $(CPPFLAGS) -c $<

engine/audio/%.o: engine/audio/%.cpp
	g++ -o $@ $(CPPFLAGS) -c $<

directx/%.o: directx/%.cpp
	g++ -o $@ $(CPPFLAGS) -c $<

cannonboard/%.o: cannonboard/%.cpp
	g++ -o $@ $(CPPFLAGS) -c $<

clean:
	delete $(OBJ) 
 