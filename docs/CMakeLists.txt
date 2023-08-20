
# NOTE: The order of this list determines the order of items in the Guides
#       (i.e. Pages) list in the generated documentation
<<<<<<< HEAD
set(GLFW_DOXYGEN_SOURCES
    "include/GLFW/glfw3.h"
    "include/GLFW/glfw3native.h"
    "docs/main.dox"
    "docs/news.dox"
    "docs/quick.dox"
    "docs/moving.dox"
    "docs/compile.dox"
    "docs/build.dox"
    "docs/intro.dox"
    "docs/context.dox"
    "docs/monitor.dox"
    "docs/window.dox"
    "docs/input.dox"
    "docs/vulkan.dox"
    "docs/compat.dox"
    "docs/internal.dox")

# Format the source list into a Doxyfile INPUT value that Doxygen can parse
foreach(path IN LISTS GLFW_DOXYGEN_SOURCES)
    set(GLFW_DOXYGEN_INPUT "${GLFW_DOXYGEN_INPUT} \\\n\"${GLFW_SOURCE_DIR}/${path}\"")
=======
set(source_files
    main.dox
    news.dox
    quick.dox
    moving.dox
    compile.dox
    build.dox
    intro.dox
    context.dox
    monitor.dox
    window.dox
    input.dox
    vulkan.dox
    compat.dox
    internal.dox)

set(extra_files DoxygenLayout.xml header.html footer.html extra.css spaces.svg)

set(header_paths
    "${GLFW_SOURCE_DIR}/include/GLFW/glfw3.h"
    "${GLFW_SOURCE_DIR}/include/GLFW/glfw3native.h")

# Format the source list into a Doxyfile INPUT value that Doxygen can parse
foreach(path IN LISTS header_paths)
    string(APPEND GLFW_DOXYGEN_INPUT " \\\n\"${path}\"")
endforeach()
foreach(file IN LISTS source_files)
    string(APPEND GLFW_DOXYGEN_INPUT " \\\n\"${CMAKE_CURRENT_SOURCE_DIR}/${file}\"")
>>>>>>> source/master
endforeach()

configure_file(Doxyfile.in Doxyfile @ONLY)

add_custom_command(OUTPUT "html/index.html"
                   COMMAND "${DOXYGEN_EXECUTABLE}"
                   WORKING_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}"
                   MAIN_DEPENDENCY Doxyfile
                   DEPENDS ${header_paths} ${source_files} ${extra_files}
                   COMMENT "Generating HTML documentation"
                   VERBATIM)

add_custom_target(docs ALL SOURCES "html/index.html")
set_target_properties(docs PROPERTIES FOLDER "GLFW3")

set_target_properties(docs PROPERTIES FOLDER "GLFW3")

