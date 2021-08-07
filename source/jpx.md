
# JPX

## What is JPX?

JPX is a framework for JPizza2 that allows you to create and build projects that devices
without JPizza can run. 

## Creating a New JPX Project

To create a new project, simply type `jpx create <projectName>` in the command line.
This creates a directory titled whatever you named your project with two subdirectories inside.
- *src*
- *build*

The *src* directory is where you will write all your code. It contains a *main.devp* file, which
is where your main program execution will be written.

The *build* directory is where JPX will transpile your JPX code into JPizza code, and set up
everything for deployment.

## Compiling Your JPX Project

In the directory where your project directory is located, (*NOT inside the project directory*), run the command line command
`jpx build <projectName>`. This will compile your project into a single file and remove any empty directories.

## Bonus JPX Feature

JPX allows you to import files from subdirectories by doing `import subdirectory.file;`.
