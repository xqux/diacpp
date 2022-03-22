# DiaCpp

## About
**DiaCpp** — program for displaying block diagrams from local files, 
written in C++17 using the Qt framework.

## Project structure
The project uses the MVP pattern to organize communication with users.

The data model and presentation are intentionally separated to provide system flexibility. 
Using the structure of this application, it would even be possible to separate user input from output. 
This particular implementation doesn't emphasize this feature using the Qt framework.

## Dependencies
* 5.15.2 ≤ Qt ≤ 6.2.3;
* CMake 3.5+.

The project was successfully built and run on Fedora Gnome 35 with Qt packages installed, 
but should work correctly on any compatible platform: GNU/Linux, Microsoft Windows, macOS and BSD.

It's recommended to run in **Qt Creator**.

## Supported Formats
For an example of work, we use:
* **Pseolang** as a diagram parser language;
* **Pseorend** as a diagram display render.

There is a consistent interface between these modes that 
describes all the elements and how they interact with each other.

### Pseolang
<pre>
0. comment   | Your custom text
1. alg       | Begin/End
2. action    | a: int = 10
3. io        | a := input(), b := input()
4. condition | a > 0
5. cycle     | while a != 10
</pre>

**The syntax is**:
1. The program reads the first first word of the string and compares it with the operations;
2. Some number of spaces are read;
3. Service non-word characters are read (e.g. -, |, :, >>);
4. Some number of spaces are read;
5. Everything that comes next is the text on the object.

You can look in the examples directory. 
Try loading the files into the program to fully understand the commands.

### Pseorend
...

## Logging
All statuses (errors, warnings, successes) are automatically added to the report.log file.
