# Paths
JDK_DIR=C:\Program Files\Java\jdk1.6.0_19
LUA_DIR=C:\Users\Public\Apps\Lua\5.2\lib64
VERSION=52

# Tools
CC=cl
LD=link
MT=mt

# Default arguments
CFLAGS=/nologo /c /O2 /GL /W3 /DNDEBUG
LDFLAGS=/nologo /DLL /LTCG
MTFLAGS=-nologo

# Description blocks
all: jnlua$(VERSION).dll

jnlua$(VERSION).dll: jnlua.obj
	$(LD) $(LDFLAGS) /OUT:jnlua$(VERSION).dll /LIBPATH:"$(LUA_DIR)" lua$(VERSION).lib jnlua.obj
	$(MT) $(MTFLAGS) -outputresource:jnlua$(VERSION).dll;2 -manifest jnlua$(VERSION).dll.manifest 

jnlua.obj: ..\jnlua.c
	$(CC) $(CFLAGS) /MD /DLUA_BUILD_AS_DLL /I"$(JDK_DIR)\include" /I"$(JDK_DIR)\include\win32" /I"$(LUA_DIR)\include" ..\jnlua.c

clean:
	-del jnlua$(VERSION).dll jnlua$(VERSION).dll.manifest jnlua$(VERSION).exp jnlua$(VERSION).lib jnlua.obj