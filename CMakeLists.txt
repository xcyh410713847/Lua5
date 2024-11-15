# #########################################################################
# 文件: CMakeLists.txt
# 作者: shyfan
# 日期: 2024/11/15 21:07:02
# 功能: Lua 源码编译
# #########################################################################

# 需求的CMake版本
CMAKE_MINIMUM_REQUIRED(VERSION 3.5)

# 项目名称
PROJECT(Lua)

# 编译完成后拷贝到指定目录
macro(CopyToTarget TargetName)
    add_custom_command(TARGET ${TargetName} POST_BUILD
            COMMAND ${CMAKE_COMMAND} -E copy
            $<TARGET_FILE:${TargetName}>
            ${CMAKE_SOURCE_DIR}/bin/$<TARGET_FILE_NAME:${TargetName}>
        )
endmacro()

# 增加子目录
ADD_SUBDIRECTORY(src)
