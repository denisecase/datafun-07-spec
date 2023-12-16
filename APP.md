# Option 2. Applied Data Analytics: APP

App. Interactive Analytics App using Shiny for Python: Get introduced to creating interactive web applications with Shiny for Python. This choice focuses on building basic interactive tools for data analysis.

Here's the missing part of the general specification. This goes after the logging section.
Renumber the sections to be consistent with the outline in the general specification.

## Module Specification

### Requirements

#### 5. Data Acquisition

Read about Shiny for Python. 
Go to the Examples, and find "Read local CSV".

Notice there are two files in this example:

app.py and mtcars.csv.

The entire app code is below.

You know the imports - the only thing new is we import App, render, and ui from shiny. 

Then, we define the app_ui as a fluid page with a single table output.

Then, we define the server function to determine what makes up the table. In this case, it's the second mtcars.csv file.

Run it and we see the table. 

```python
from pathlib import Path

import pandas
from shiny import App, render, ui

app_ui = ui.page_fluid(
    ui.output_table("table"),
)


def server(input, output, session):
    @output
    @render.table
    def table():
        infile = Path(__file__).parent / "mtcars.csv"
        df = pandas.read_csv(infile)
        # Use the DataFrame's to_html() function to convert it to an HTML table, and
        # then wrap with ui.HTML() so Shiny knows to treat it as raw HTML.
        return df


app = App(app_ui, server)
```

#### 6. Add an Input Widget to the App ui

Add an input slider to the input ui.
Provide the logic in the server function to provide reactive output.
Add the reactive output to the ui, above the table.

For example:

```python
from pathlib import Path

import pandas
from shiny import App, render, ui

app_ui = ui.page_fluid(
    ui.input_slider("x", "Minimum Displacement", min=0, max=500, value=100),
    ui.output_text("out_text"),
    ui.output_table("table"),
)


def server(input, output, session):

    @output
    @render.text
    def out_text():
        return f"Showing cars with displacement > {input.x()}"


    @output
    @render.table
    def table():
        infile = Path(__file__).parent / "mtcars.csv"
        df = pandas.read_csv(infile)
        filtered_df = df[df['disp'] >= input.x()] # Filter based on slider
        return filtered_df

app = App(app_ui, server)
```

#### 7. Customize the Widget to Limit Displacement

Modify the slider so it refers to the displacement column in the table.
Sliding it will set the minimum displacement for the table.

For example:

```python
app_ui = ui.page_fluid(
    ui.input_slider("min_disp", "Minimum Displacement", min=0, max=df['disp'].max(), value=100),
    ui.output_text("out_text"),
    ui.output_table("table"),
)
```

#### 8. Provide Slider Logic in the Server Function

Customize the server logic so the slider will set the minimum displacement for the table.

For example:

```python

from pathlib import Path
import pandas
from shiny import App, render, ui

app_ui = ui.page_fluid(
    ui.input_slider("min_displacement", "Minimum Displacement", min=0, max=500, value=100),
    ui.output_text("out_min_displacement_text"),
    ui.output_table("table"),
)

def server(input, output, session):
    @output
    @render.text
    def out_min_displacement_text():
        return f"Showing cars with displacement > {input.min_displacement()}"
        
    @output
    @render.table
    def table():
        infile = Path(__file__).parent / "mtcars.csv"
        df = pandas.read_csv(infile)
        filtered_df = df[df['disp'] >= input.min_displacement()] # Filter based on slider
        return filtered_df

app = App(app_ui, server)
```

#### 9. Storytelling and Presentation

Interpret the process and results to craft a narrative around your findings.
Add additional visualizations and widgets.
Consider questions such as:

- Why interact with a chart?
- What kind of input widgets would be useful?
- What kind of outputs would be useful?
- What logic do I need to provide in the server function to make this work?
- What insights can be gained from adjusting the slider?

Present your findings in a logical and engaging manner.

## Shiny Concepts

Understand the basics of Shiny, including its structure consisting of a User Interface (UI) and a Server function:

- UI: Defines the layout and appearance of your app.
- Server: Contains the instructions to reactively compute outputs.

Terms:

- A widget is a control. There are many types of widgets. Sliders, buttons, and text boxes are all examples of widgets.
- A reactive expression is a function that returns a value. It can be used to create a reactive output.
- A reactive output is a value that can be used as input to other reactive expressions, or as output to the UI.
- A reactive function is a function that returns a reactive expression.


Annotations are concise ways to apply functions to the UI.

```python
@output - marks it as output
@render.text - says to render this (display this) as text
@render.table - says to render this (display this) as a table
```

Important: Note the way variable names link to functions. 
For example, input.x() is the value of the input widget named x. 

Find all uses of widget names in the ui:

- "x"
- "min_displacement"
- "out_min_displacement_text"
- "table"

Find all uses of server functions in the server:

- out_min_displacement_text()
- table()

Find all uses of input functions (used in the server functions):

- input.x()
- input.min_displacement()

Change these to be more descriptive so we can add more interactions. 

```python
from pathlib import Path
import pandas
from shiny import App, render, ui

app_ui = ui.page_fluid(
    ui.input_slider("min_displacement", "Minimum Displacement", min=0, max=500, value=100),
    ui.output_text("out_min_displacement_text"),
    ui.output_table("table"),
)

def server(input, output, session):
    @output
    @render.text
    def out_min_displacement_text():
        return f"Showing cars with displacement > {input.min_displacement()}"
        
    @output
    @render.table
    def table():
        infile = Path(__file__).parent / "mtcars.csv"
        df = pandas.read_csv(infile)
        filtered_df = df[df['disp'] >= input.min_displacement()] # Filter based on slider
        return filtered_df

app = App(app_ui, server)
```

with Shiny apps, we "wire things up" or configure our user interface.
It's pretty fun (and very powerful).
