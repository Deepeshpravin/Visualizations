# Visualizations

Both the chord diagram and sankey plots are effective visualization tools to
understand the interrelationships between different entities.

# Chord diagram
Holoviews is a popular package to plot the chord diagrams.
The data to plot a chord diagram should have three columns - Source, Target and Frequency.
The chords are plotted from Source to Target with the thickness proportional to the value
in the Frequency column. The plotted chord diagram can be saved as an interactive html file.


# Sankey plots
The Sankey diagrams are plotted using plotly. To create a Sankey plot, one needs 
a list of data labels, a list of indices of the source labels and another list 
of indices of the target labels. The indices of the source labels should be repeated
depending on the number of target labels they are going to get connected. For example,
if the first source element has connections to three different target elements, then
'0' should be repeated three times on the source list. If the 0th source element is
going to be connected to 3rd, 4th and 5th target elements, then the first three indices
on the target list are going to be 3, 4, and 5. Lastly, we also need a list of values.
Each ith value represents the strength of the connection between ith source element
and ith target element.
Colors can also be assigned for each link using the hex codes.
The plotted sankey diagram can be saved both as a png file as well as an interactive
html file.
