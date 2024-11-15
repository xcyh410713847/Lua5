# #########################################################################
# 文件: src\CMakeLists.txt
# 作者: shyfan
# 日期: 2024/11/15 21:06:47
# 功能: Lua 源码编译
# #########################################################################

# 编译Lualib
FILE(GLOB dir_lualib_src *.c)
LIST(REMOVE_ITEM dir_lualib_src "lua.c" "luac.c")   # 移除lua.c和luac.c
ADD_LIBRARY(lualib STATIC ${dir_lualib_src})
CopyToTarget(lualib)

# 编译lua.c
ADD_EXECUTABLE(lua lua.c)
TARGET_LINK_LIBRARIES(lua lualib)
CopyToTarget(lua)

# 编译luac.c
ADD_EXECUTABLE(luac luac.c)
TARGET_LINK_LIBRARIES(luac lualib)
CopyToTarget(luac)
