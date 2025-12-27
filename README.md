## minilineplot

minilineplot.py is a single Python module, with no dependencies, producing an SVG image of a chart with one or more plotted lines.

The chart has a left vertical axis and a bottom horizontal axis, grid lines are possible,

Two classes are defined.

**Line**, containg x,y points which creates a line to be plotted 

**Axis** which creates the axis, and to which Line objects can be added.

The Axis class has methods to create an svg string suitable for embedding in an html document
it can also create an svg image, either as a bytes object, or saved to a file.

# Line

Arguments

*values*  a list of x,y tuples

*color*  an SVG color of the line

*stroke*  line width, 1 for a thin line.

*label*  A label string for a key, if not given, the key will not be drawn


If the Axis 'xstrings' argument is set as strings along the x axis,
for example months of the year, then the Line values tuples should be:
x  is a percentage along the x axis, y is the actual value.

so [(0,59), (100,28)]  is a line from

the extreme left (0%) value 59 to the extreme right (100%) value 28

If the Axis x axis is defined as numbers rather than strings then each (x,y) tuple should be the numeric values to be plotted.

color is an SVG color, using standard strings such as

Color Names: "red", "blue" etc.

Hex Codes: "#FF0000" for red.

RGB/RGBA: "rgb(255,0,0)" or "rgba(255,0,0,0.5)" (with opacity).

HSL/HSLA: "hsl(0,100%,50%)" or "hsla(0,100%,50%,0.5)" (hue, saturation, lightness, alpha)


# Axis

Arguments

*lines* list of Line objects

*fontsize"  default 24

*imagewidth*  default 800

*imageheight* def:int = 600

    xstrings:list[str] = field(default_factory=list)   # A list of strings used as the x axis values, use for text values such as months, etc.,
                                                       # If any strings are set here, the following xaxis numbers are ignored

    #### or use numbers for the x axis ####

    xformat:str = ".2f"            # How the x axis numbers are formatted,
    xmin:float|int = 0             # minimum x value
    xmax:float|int = 10            # maximum x value
    xintervals:int = 5             # interval spacing of values along the x axis, 5 would be five intervals and six values.

    # The y axis is always just numbers

    yformat:str = ".2f"            # How the y axis numbers are formatted,
    ymin:float|int = 0             # minimum y value
    ymax:float|int = 10            # maximum y value
    yintervals:int = 5             # interval spacing of values up the y axis, 5 would be five intervals and six values.


    title:str = ""                 # printed at the top of the chart
    description:str = ""           # printed at the bottom of the chart

    verticalgrid:int = 1           # 0 is no vertical grid lines, 1 is a line for every x axis interval, 2 is a line for every second interval.
    horzontalgrid:int = 1          # 0 is no horizontal grid lines, 1 is a line for every y axis interval, 2 is a line for every second interval.

    # The following colors are SVG colors, using standard strings

    gridcol:str="grey"             # Color of the chart grid
    axiscol:str="black"            # Color of axis, title and description
    chartbackcol:str="white"       # the background colour of the chart
    backcol:str="white"            # The background colour of the whole image


    # xformat and yformat is a format string describing how numbers are printed
    # for example the string ".2f"   gives a number to two decimal places

