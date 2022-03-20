# DiaCpp

## About
**DiaCpp** — program for displaying block diagrams from local files.

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
* **Pseolang** as a parser language;
* **Pseorend** as a diagram renderer.

There is a consistent interface between these modes that 
describes all the elements and how they interact with each other.

### Pseolang
<pre>
1. alg       | Begin/End
2. action    | a := 3
3. condition | a > 3
4. io        | a := input()
5. cycle     | for el in 0..5: TO_DO...
</pre>

You can look in the examples directory. 
Try loading the files into the program to fully understand the commands.

### Pseorend
...
