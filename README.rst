===========================================
Papyrus Assembly package for Sublime Text 2
===========================================

:Author: Cipscis (Mark Hanna)

:Contact: mark@cipscis.com

:Version: 1.5

Description
===========
This is a package for Sublime Text 2 that makes it easier to view Papyrus assembly files (file extension ``.pas``). Papyrus is the scripting language used by the video game Skyrim, which can be modified via the `Creation Kit <http://www.creationkit.com/>`_. These files can be generated in 2 ways:

- Running the Papyrus compiler with either the ``-keepasm`` or ``-asmonly`` command line arguments. The former compiles the script but keeps the assembly file, whereas the latter does not compile the script and only generates the assembly file.

- Running the Papyrus assembler with the ``-D`` command line argument to disassemble a compiled script (file extension ``.pex``).

Papyrus assembly can be converted into fully compiled Papyrus scripts by running it through the Papyrus assembler. A build system is included in the package to make this easy.

Installation
============
Extract the "Papyrus Assembly" folder into the Packages directory for your Sublime Text 2 installation. This directory can be opened easily by selecting ``Preferences > Browse Packages...`` in Sublime Text 2.

That's it. Now you should be able to open files with the ``.pas`` extension in Sublime Text 2 and they'll automatically use the syntax highlighting I've defined.

A build system for disassembling compiled Papyrus files is also included in this package.

Update
------
- < 1.4 to >= 1.4
  - If you're updating to version 1.4 or higher from a version prior to 1.4, you should also delete the following file from your Packages/User directory:
  ``Disassemble Papyrus.sublime-build``
- 1.4 to 1.5
  - If you're updating from version 1.4 to version 1.5, you should also delete the ``Compiled Papyrus`` directory from your Packages directory.

Uninstallation
==============
Just delete the ``Papyrus Assembly`` folder from your Packages directory to uninstall this package.

Use
===
To assemble these files into fully compiled scripts, press your ``Build`` keyboard shortcut (``Ctrl+B`` or ``F7`` both work by default) or select ``Build`` under ``Tools``. For this to work, either ``Papyrus Assembly`` or ``Automatic`` need to be selected under ``Tools > Build System``.

To use the ``Disassemble Papyrus`` build system to generate assembly files from compiled scripts, open up the compiled script in Sublime Text 2 (it should have a file extension of ``.pex``), just run the build system either from ``Build`` under ``Tools`` or via the keyboard shortcut. Either ``Disassemble Papyrus`` or ``Automatic`` should be selected under ``Tools > Build System``.

If either of the build packages doesn't work right away, you may need to alter them to match your Skyrim installation directory. Open up the relevant ``.sublime-build file`` and edit the path to match your Skyrim installation directory.

Generating Assembly Files
-------------------------
If you're a Sublime Text 2 user and a Papyrus scripter, you probably already have the Papyrus build system set up, thanks to the instructions on the Creation Kit Wiki. If not, I suggest you do that now - `Sublime Text Setup <http://www.creationkit.com/Sublime_Text_Setup>`_

Note that the Papyrus Compiler and Papyrus Assembler are both components of the Creation Kit.

In order to easily generate Papyrus assembly files, I recommend you manually edit your ``ScriptCompile.bat`` file (in the ``Papyrus Compiler`` folder in your Skyrim installation directory) to include the ``-keepasm`` command line argument.

Assembly files are generated in the same folder as the compiled script, not the source.

Here is the usage information for the Papyrus compiler as reported via its ``-?`` command line argument::

		Usage:
		PapyrusCompiler <object or folder> [<arguments>]

		  object     Specifies the object to compile. (-all is not specified)
		  folder     Specifies the folder to compile. (-all is specified)
		  arguments  One or more of the following:
		   -debug|d
		    Turns on compiler debugging, outputting dev information to the screen.
		   -optimize|op
		    Turns on optimization of scripts.
		   -output|o=<string>
		    Sets the compiler's output directory.
		   -import|i=<string>
		    Sets the compiler's import directories, separated by semicolons.
		   -flags|f=<string>
		    Sets the file to use for user-defined flags.
		   -all|a
		    Invokes the compiler against all psc files in the specified directory
		    (interprets object as the folder).
		   -quiet|q
		    Does not report progress or success (only failures).
		   -noasm
		    Does not generate an assembly file and does not run the assembler.
		   -keepasm
		    Keeps the assembly file after running the assembler.
		   -asmonly
		    Generates an assembly file but does not run the assembler.
		   -?
		    Prints usage information.

Here is the usage information for the Papyrus assembler as reported via its ``-?`` command line argument::

		Usage:
		PapyrusAssembler object [-D] [-V] [-Q] [-A] [-S] [-?]

		  object  Specifies the object to be assembled or disassembled. Assembly looks
		          for a ".pas" extension. Disassembly looks for a ".pex" extension.
		  -D      Disassembles the object, instead of assembling it.
		  -V      Turns on verbose mode.
		  -Q      Turns on quiet mode. (No status messages, only errors)
		  -A      Do not assemble/disassemble the file, just load and analyze.
		  -S      Strips debugging info from a compiled file. Cannot be used with -A
		          or -D
		  -?      Prints this usage information

Keep in mind that the compiler expects a file extension, whereas the assembler expects the file name **without** an extension.

Change Log
==========
- 1.0 - 12th September 2012

  + Initial Release

- 1.1 - 12th September 2012

  + Added syntax highlighting for semicolon line comments outside of code. These comments are generated in disassembled files generated by the assembler, not assembly files generated by the compiler

  + Fixed terminology for assembly files generated by the assembler - should read "disassembled", not "decompiled". Renamed ``Decompile Papyrus`` build system to ``Disassemble Papyrus``

- 1.2 - 14th September 2012

  + Added ``ARRAYFINDELEMENT`` and ``ARRAYRFINDELEMENT`` array operators

- 1.3 - 25th September 2012

  + Added ``JUMPT`` (``JUMP`` if ``True``) instruction

- 1.3.1 - 25th September 2012

  + Made highlighting case-insensitive, so highlighting is also applied to disassembled files, for example

- 1.4 - 26th September 2012

  + Added blank syntax highlighting for compiled Papyrus and updated "Disassemble Papyrus" build sytem. This means ``.pex`` files can be opened in Sublime Text 2 and the ``Disassemble Papyrus`` build system will automatically be used. This build file has been moved from the ``User`` directory into its own package.

- 1.5 - 2nd October 2012

  + Added highlighting for escaped characters in strings. In particular, this prevents strings containing a double quote (escaped as ``\"``) from causing issues with strings not closing correctly.

  + Combined both ``Papyrus Assembly`` and ``Compiled Papyrus`` into a single package, as there was no benefit to separating them.

  + Removed case sensitivity from non-code assembly markup.

  + Removed inappropriate entity labelling to fix symbol search.

  + Added highlighting for incomplete lines for when you're writing your own assembly code.

Permissions
===========
Feel free to edit and redistribute this file (in edited or unedited form) anywhere you like without contacting me. I ask only the following:

- Include adequate documentation, preferably this readme (potentially modified as appropriate)

- Please provide a link to the original download location on Skyrim Nexus

- If the package is unedited, please credit me as the author

- If the package is edited, please credit me as the author of the original package and include in your documentation the version number of the package that you used as a template for your modified package