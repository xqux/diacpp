# DiaCpp

## About
**DiaCpp** — program for displaying block diagrams from local files, 
written in C++17 using the Qt framework.

## Project Structure
The project uses the MVP pattern to organize communication with users.

The data model and presentation are intentionally separated to provide system flexibility. 
Using the structure of this application, it would even be possible to separate user input from output. 
This particular implementation doesn't emphasize this feature using the Qt framework.

## Dependencies
* [x] **C++ version**: 17+;
* [x] **Qt version**: 5.15.2 ≤ Qt ≤ 6.2.3;
* [x] **CMake version**: 3.5+;
* [x] **Compilers**: gcc, clang.

The project was successfully built and run on Fedora Gnome 35 with Qt packages installed, 
but should work correctly on any compatible platform: GNU/Linux, Microsoft Windows, macOS and BSD.

It's recommended to run in **Qt Creator**.

To change Qt to version 6, uncomment the line in the CMake file.

## Supported Formats
For an example of work, we use:
* **Pseolang** as a diagram parser language;
* **Pseorend** as a diagram display render.

There is a consistent interface between these modes that 
describes all the elements and how they interact with each other.

### Pseolang
#### Syntax

| Instruction | Activity                                      | Description                                                                       |
| ----------- | --------------------------------------------- | --------------------------------------------------------------------------------- |
| #           | My TRA LA LA                                  | The comment that contains your custom noshowd text                                |
| alg         | Solving the mathematical problem              | The start/end of the algorithm that contains diagram text                         |
| process     | const a: int = 10<br/>var b, c<br/>d += a + 1 | The process of the algorithm that contains diagram text                           |
| io          | a := input()<br/>output(a)                    | The input/output process of the algorithm that contains diagram text              |
| decision    | ¬(a > 0 ∧ a ≠ 10)                             | The condition (if-statement) of the algorithm that contains diagram text          |
| loop        | label-1                                       | The cycle of the algorithm (makes a label for the jump / jumps to the loop label) |
| =>          | True<br/>YES<br/>Off                          | Mark the next arrow with the text (by default, arrows contain no text)            |



#### Parsing Process
1. The parser reads the indent ...
2. The parser reads the first first word of the string and compares it with the operations;
3. Some number of spaces are read;
4. Service non-word characters are read (e.g. -, |, :, ::, >>, ->);
5. Some number of spaces are read;
6. Everything that comes next is the text on the object.

You can look in the examples directory. 
Try loading the files into the program to fully understand the commands.

### Pseorend
...

## Logging
All statuses (errors, warnings, successes) are automatically added to the report.log file.
