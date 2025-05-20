# squad-analysis
Python scripts for generating analysis images of squad make-ups (based on those by The Athletic)

##  Instructions
### Setup input files
Before setting doing anything within the script itself .csv files containing the squad information and the formation need to be created. The squad details csv must contain the columns shown in the table below. Date of Birth has also been included in the example file but isn't used in the squad depth script (for planned future chart).

| First Name  | Last Name | Position | Contract Expiry | Status |
| :----------- | :----------- | :----------- | :----------- | :----------- |
| Players first name | Players last  name | Position, must match a name given in the formation .csv | Year in which contract expires. E.g. if end of 25/26 seasons use 2026. | Squad status, uses a single capital letter. The following options are available: <ul><li>N - No status (under contract and at the club)</li><li>S - New signing for that season.</li><li>I - Player loaned in.</li><li>O - Player loaned out.</li></ul> |

The formation .csv is used to lay out the positions and players on the graphic. It requires 3 columns: name, x and y. The data in the name column is what will show in the box for each position, and is used to filter the squad list when placing players (therefore you must be consistent between your formation and squad csv files). the x and y columns contain coordinates for locating each position on the pitch. The pitch is split into 100 even units in both directions, choosing coordinates can take a little trial and error, use the formation csv included for help.

### Specifying in script inputs

### Customising Colours



## Acknowledgements
Most of the heavy lifting is really done by the [mplsoccer](https://mplsoccer.readthedocs.io/en/latest/index.html) library. They have lots of good documentation and examples if you want to create your own plots or edit this one. The scripts shared by [McKay Johns](https://github.com/mckayjohns/youtube-videos/tree/main) were also helpful examples for using mplsoccer.
