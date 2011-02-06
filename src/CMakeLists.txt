# We define a set here to hold all of the source files we want to compile. This
# is done mostly for convenience and future-proofing

set(stjerm_srcs config.c main.c mainwindow.c popupmenu.c shortcut.c stjerm.h term.c)

# Here, we compile all of the source files into the stjerm executable.

add_executable(stjerm ${stjerm_srcs})

