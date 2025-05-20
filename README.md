# Squad Makeup Analysis Scripts
Python scripts for generating analysis images of squad make-ups (based on those done by The Athletic).

##  Instructions - Squad Depth
### Setup input files
Before setting doing anything within the script itself .csv files containing the squad information and the formation need to be created. The squad details csv must contain the columns shown in the table below. Date of Birth has also been included in the example file but isn't used in the squad depth script (for planned future chart).

| First Name  | Last Name | Position | Contract Expiry | Status |
| :----------- | :----------- | :----------- | :----------- | :----------- |
| Players first name | Players last  name | Position, must match a name given in the formation .csv | Year in which contract expires. E.g. if end of 25/26 seasons use 2026. | Squad status, uses a single capital letter. The following options are available: <ul><li>N - No status (under contract and at the club)</li><li>S - New signing for that season.</li><li>I - Player loaned in.</li><li>O - Player loaned out.</li></ul> |

The formation .csv is used to lay out the positions and players on the graphic. It requires 3 columns: name, x and y. The data in the name column is what will show in the box for each position, and is used to filter the squad list when placing players (therefore you must be consistent between your formation and squad csv files). the x and y columns contain coordinates for locating each position on the pitch. The pitch is split into 100 even units in both directions (y is vertical from the goal line, x runs right to left), choosing coordinates can take a little trial and error, use the formation csv included for help.

### Specifying in script inputs
The Jupyter Notebook file contains an input cell where the team name (for display purposes), year the season starts and a link to the squad csv can be defined.  Update these prior to running.

If desired the title and subtitle of the image can also be tweaked in this section. The script is setup to input the defined team name and season into the given title as the "title" and "subtitle" variables.

### Customising Appearance

In the input section the colour palette is also definied, if colours want to be adjusted this is the easiest place to do it. If you want to change which colours are used where this is done in the main plotting section. For which colours are assigned to different squad status this can be changed be editing the colour palette references in the *status_colours* and *plot_key* variables.

The current colour palette is as follows:
<p style="background-color:#000000">Background - Used for the image background.</p>
<p style="background-color:#FFFFFF; color:#333">Foreground - Used for the main text.</p>
<p style="background-color:#999999; color:#333">cl_secondary - Used for subtitles and expiring contracts.</p>
<p style="background-color:#d61f34; color:#fff">cl_alt_1 - Used for position boxes and new signings.</p>
<p style="background-color:#3A86FF; color:#fff">cl_alt_2 - Used for loans in.</p>
<p style="background-color:#FFBE0B; color:#333">cl_alt_3 - Used for loans out.</p>
<p style="background-color:#3EC300; color:#333">cl_alt_4 - Currently unused.</p>
<p style="background-color:#595959; color:#fff">cl_alt_5 - Currently unused.</p>

The fonts can also be changed by altering the *title_font* and *body_font* variables in the input section, they should reference a font installed on your system, more info on this can be found [here](https://matplotlib.org/stable/api/font_manager_api.html#).

Finally the styling of the box showing the position name and location can be adjusted by editing the box style in the bbox definition of the following section of code:

    ax2.text(
        x=row[1]["x"],
        y=row[1]["y"]+4,
        s=row[1]["name"],
        color=colours["cl_foreground"],
        bbox=dict(boxstyle="round", fc=colours["cl_alt_1"]),
        fontsize=10,
        fontweight='bold',
        fontproperties=title_font, 
        family='serif',
        ha='center',
        va='center'
    )

## Acknowledgements
Most of the heavy lifting is really done by the [mplsoccer](https://mplsoccer.readthedocs.io/en/latest/index.html) library. They have lots of good documentation and examples if you want to create your own plots or edit this one. The scripts shared by [McKay Johns](https://github.com/mckayjohns/youtube-videos/tree/main) were also helpful examples for using mplsoccer.
