
# Fridge

## What is Fridge?

Fridge is a package manager for JPizza that allows you to upload your own packages and
download others.

## Installation

First, download the latest ZIP release from the repository. Then extract it into a directory of
your choosing and add it to your PATH.

You can run Fridge by  typing `frdge.py`, and upon the first run you will need to give it
the directory where your JPizza JAR/exe is located.

## How to Upload Packages

First, package your scripts into a zip folder with the same name as the main script.

Next, open a command line prompt in the same directory and run `frdge.py` to open the Fridge
interface. Run the command `send <yourZipFile>.zip` to start the upload process.

### Keys

Keys are passwords for your packages. When you first upload your package, it will ask for a key.
Whatever you type will permanently become the package key.

If you are updating a pre-existing package, you must enter the same key as the first upload.
If you enter the incorrect key, you will not be able to upload your package.

### Dependencies

The interface will then ask for dependencies. If your program relies on any Fridge packages,
you must type them out one by one, pressing enter after each.

Once you are done, or if you have no dependencies, type `|end|` and press enter.

Congratulations! Your package is now available to all JPizza users!

## How to Download Packages

Downloading packages is simple. Open a new command line prompt and type `frdge.py` to open the
Fridge interface. Type the command `get <packageName>` to download the specified package.
The package and its dependencies will be installed, and are now usable in your programs.
