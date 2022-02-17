# CMakeLists files in this project can
# refer to the root source directory of the project as ${HELLO_SOURCE_DIR} and
# to the root binary directory of the project as ${HELLO_BINARY_DIR}.
cmake_minimum_required (VERSION 2.8.11)
project (QuickFix)

# Recurse into the "Hello" and "Demo" subdirectories. This does not actually
# cause another cmake executable to run. The same process will walk through
# the project's entire directory structure.
# add_subdirectory (C++)

#Create a library called "Hello" which includes the source file "hello.cxx".
# The extension is already found. Any number of sources could be listed here.
# add_library (libQuickFix
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/DataDictionary.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/DataDictionaryProvider.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/Dictionary.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/FieldConvertors.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/FieldMap.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/FieldTypes.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/FileLog.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/FileLog.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/FileStore.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/Group.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/HttpConnection.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/HttpMessage.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/HttpParser.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/HttpServer.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/Initiator.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/Log.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/Message.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/MessageSorters.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/MessageStore.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/MySQLLog.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/MySQLStore.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/NullStore.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/OdbcLog.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/OdbcStore.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/Parser.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/PostgreSQLLog.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/PostgreSQLStore.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/PUGIXML_DOMDocument.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/pugixml.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/Session.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/SessionFactory.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/SessionSettings.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/Settings.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/SocketAcceptor.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/SocketConnection.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/SocketConnector.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/SocketInitiator.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/SocketMonitor.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/SocketServer.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/SSLSocketAcceptor.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/SSLSocketConnection.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/SSLSocketInitiator.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/stdafx.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/strptime.c
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/ThreadedSocketAcceptor.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/ThreadedSocketConnection.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/ThreadedSocketInitiator.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/ThreadedSSLSocketAcceptor.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/ThreadedSSLSocketConnection.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/ThreadedSSLSocketInitiator.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/TimeRange.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/Utility.cpp
#  ${CMAKE_CURRENT_SOURCE_DIR}/C++/UtilitySSL.cpp
# )

set(CMAKE_C_COMPILER "gcc-11")
set(CMAKE_CXX_COMPILER "/usr/bin/g++-11")

#set(CMAKE_C_STANDARD 17 CACHE STRING "C standard to be used")
set(CMAKE_CXX_STANDARD 20 CACHE STRING "C++ standard to be used")
# Add executable called "helloDemo" that is built from the source files
# "demo.cxx" and "demo_b.cxx". The extensions are automatically found.
add_executable (compile_bin main.cpp)

# Link the executable to the Hello library. Since the Hello library has
# public include directories we will use those link directories when building
# helloDemo
target_link_libraries (compile_bin LINK_PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/../lib/libquickfix.a)

# Make sure the compiler can find include files for our Hello library
# when other libraries or executables link to Hello
target_include_directories (compile_bin PUBLIC
 ${CMAKE_CURRENT_SOURCE_DIR}/../include/quickfix
)

add_definitions(
  -DHAVE_STD_UNIQUE_PTR
  -DHAVE_STD_SHARED_PTR
)
