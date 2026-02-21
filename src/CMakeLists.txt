# MIT License
#
# Copyright (c) 2007-2023 Lua.org, PUC-Rio.
# Copyright (c) 2024-2026 The OneLuaPro project authors.
#
# Permission is hereby granted, free of charge, to any person obtaining a copy of
# this software and associated documentation files (the "Software"), to deal in 
# the Software without restriction, including without limitation the rights to 
# use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
# the Software, and to permit persons to whom the Software is furnished to do so,
# subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all 
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.

# ------------------------------------------------------------------------------
# lpeg DLL
add_library(lpeg SHARED)

# setup lua include directory
target_include_directories(lpeg PRIVATE ${LIBLUA_INCLUDEDIR})

# plattform-independend sources
target_sources(lpeg PRIVATE lpcap.c lpcode.c lpcset.c lpprint.c lptree.c lpvm.c)

# setup platform-specific sources, compile and linker options
if(WIN32 AND NOT MinGW)
  target_compile_definitions(lpeg PRIVATE
    LUA_BUILD_AS_DLL LUA_LIB
    _WINDLL _WIN32 _CRT_SECURE_NO_WARNINGS
  )
  target_link_directories(lpeg PRIVATE ${LIBLUA_LIBDIR})
  target_link_libraries(lpeg PRIVATE liblua ws2_32)
else()
  message(FATAL_ERROR "Not yet fully implemented.")
endif()

# Install
install(TARGETS lpeg RUNTIME DESTINATION ${INSTALL_TOP_CDIR})
install(FILES re.lua DESTINATION ${INSTALL_TOP_LDIR})
