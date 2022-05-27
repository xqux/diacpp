# DiaCpp

## About
**DiaCpp** — the cross-platform program and the project for displaying block diagrams from local files,
written in [C++17](https://en.cppreference.com/w/cpp/17) using the [Qt Framework](https://doc.qt.io).

## Project Structure
The project uses the ~~MVP pattern~~ to organize communication with users.

The ~~data model~~ and ~~presentation~~ are intentionally separated to provide system flexibility.
Using the structure of this application, it would even be possible to separate user input from output.
This particular implementation doesn't emphasize this feature using the [Qt Framework](https://doc.qt.io).

All qt dependencies are in a ~~separate directory~~.

### User interface
1. A global menu with the ability to upload a file;
2. Support for the drag-and-drop GUI window;
3. A diagram output in the main window;
4. Display an error in the status bar and add it to the log file.

## Dependencies
- [x] **C++ version**: 17+;
- [x] **Qt version**: 5.15.2 ≤ Qt ≤ 6.2.3;
- [x] **CMake version**: 3.5+;
- [x] **Compilers**: gcc, clang.

The project was successfully built and run on Fedora Gnome 35 with Qt packages installed,
but should work correctly on [any compatible platform](https://doc.qt.io/qt/supported-platforms.html):
GNU/Linux, Microsoft Windows, macOS and BSD.

You should to run this project in [Qt Creator](https://www.qt.io/download).

To change Qt to version 6, uncomment the line in the ~~CMake file~~.

## Formats
**The language** describes the interaction between elements. There can be several parsers for one language.

**The renderer** draws the __language representation__ according to its parameters.
Different renderers can show the same data in different ways (e.g. colors, shapes, shape directionality, etc.)

**Language representation** — a consistent interface that describes all elements and how they interact with each other.
Provided by some **language** for some **parser**.

___

For an example of work, we use:
- **Pseolang** as a diagram parser language;
- **Pseorend** as a diagram display render.

### Pseolang
Parsing is done via [regular expressions](https://en.cppreference.com/w/cpp/regex/ecmascript) using special patterns.

#### Syntax

| Instruction | Activity                                      | Description                                                                  |
| ----------- | --------------------------------------------- | ---------------------------------------------------------------------------- |
| #           | My TRA LA LA                                  | The comment that contains your custom noshowd text                           |
| alg         | Solving the mathematical problem              | The start/end of the algorithm that contains diagram text                    |
| process     | const a: int = 10<br/>var b, c<br/>d += a + 1 | The process of the algorithm that contains diagram text                      |
| io          | a := input()<br/>output(a)                    | The input/output process of the algorithm that contains diagram text         |
| decision    | ¬(a > 0 ∧ a ≠ 10)                             | The condition (if-statement) of the algorithm that contains diagram text     |
| loop        | label-1                                       | The cycle of the algorithm (makes a label for the jump / jumps to the label) |
| =>          | True<br/>YES<br/>off                          | Mark the next arrow with the text (by default, arrows contain no text)       |

//! FIXME
> **Commands** include *alg*, *process*, *io*, *decision* and *loop*.

1. The parser reads the indent ...
2. The parser reads the first first word of the string and compares it with the operations;
3. Some number of spaces are read;
4. Service non-word characters are read (e.g. -, |, :, ::, >>, ->); //! ADD ALL VARS
5. Some number of spaces are read;
6. Everything that comes next is the text on the object.

// FIXME
> **Operations** include *#* and *=>*.

1. ...
2. ..
3. .

You can look in the ~~examples directory~~.
Try loading the files into the program to fully understand the commands.

#### Remarks
- Commands are case sensitive;
- If a command is preceded by a dot, a current branch ends;
- If there is a '#' at the beginning of the line, then subsequent characters of the line are ignored;
- Instruction separators are newlines and indented spaces/tabs.

#### Messages
* 🚫 Unknown command;
* ...

### Pseorend
#### Remarks
- Text must be provided in UTF-8 format;
- Text supports ligatures;
- If the text doesn't fit on the diagram, it tries to display '···' or nothing (hover over object to see the text);
- There is a limit on the number of branches (2);
- It's possible to set the size of the figures and the length of the relations ~~through CMake~~.

#### Messages
- 🚫 Too Many Branches;
- ⚠️ Non-Fitting Text.

## Generated Files
> You can only run 1 application instance because files can't be opened for writing more than once.

There are some files that are created in the application directory.
You can turn them off or change the name in the ~~main project file~~.

By default, the program doesn't use external directories as storage.

### Logging
All statuses (errors, warnings, successes) are automatically added to the **report.log** file.

### Parameters
If the appropriate preprocessor directive is used, then a **config.ini** file is created.
This file contains the state of the application's main window.
