cmake_minimum_required(VERSION 3.12)

project(EuM-Karten NONE)
include(UseLATEX)

add_custom_target(
    writegitid ALL
    COMMAND ${CMAKE_CURRENT_SOURCE_DIR}/write-gitid.sh
    WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
)

set(IMAGE_DIRS
    img
    # Add subdirectories here
    # img/logic
    # img/rca
)

add_latex_document(Karteikarten/eum_karten.tex FORCE_PDF INCLUDE_DIRECTORIES
                   ${CMAKE_CURRENT_SOURCE_DIR}/Karteikarten/kartei DEPENDS writegitid)

# Print version
add_latex_document(Karteikarten/eum_karten_print.tex FORCE_PDF INCLUDE_DIRECTORIES
                   ${CMAKE_CURRENT_SOURCE_DIR}/Karteikarten/kartei DEPENDS writegitid)

