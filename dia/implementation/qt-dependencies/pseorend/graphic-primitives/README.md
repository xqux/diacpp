# About
This header file describes all the blocks and relations to display on the diagram.

You can use the files in this directory outside of this project,
it's a good way to build geometric primitives.

If the text doesn't fit into the primitive, then instead it will try to display "···",
if this text also doesn't fit, then nothing will be displayed.

# Figures
The main figures are stored in syntactic-blocks,
each element of which is inherited from GraphicFigure.

| Instruction | Figure        |
| ----------- | ------------- |
| alg         | ellipse       |
| process     | rectangle     |
| io          | parallelogram |
| decision    | rhomb         |



All figures building with [QRectF](https://doc.qt.io/qt-5/qrectf.html) acting as a placeholder.
Only a parallelogram also has a slope.

# Relations
There are 2 kinds of arrows,
each of which inherits from GraphicArrow and TextLimiter.

