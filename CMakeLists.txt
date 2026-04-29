cmake_minimum_required(VERSION 3.13)
project(pico_w_keypad_led C CXX ASM)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# This project source is written for Arduino-style APIs (Keypad.h, setup/loop).
# For Pico SDK builds, porting/wrapping is required.
# Keep this file as a scaffold for a future native SDK migration.

add_subdirectory(src)
