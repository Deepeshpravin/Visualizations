# install plotly

# import the dependencies
import plotly.graph_objects as go
import matplotlib.pyplot as plt
from matplotlib.sankey import Sankey

# data
# labels of rows followed by columns
label = ["High", "Medium", "Low", "High", "Medium", "Low", "Lapsed"]
# there are three source nodes, each linked to four target nodes
# since the first three nodes are source, count ranges from 0 to 2.
source = [0,0,0,0,1,1,1,1,2,2,2,2]
# there are four target nodes linking with three source nodes
# since the last four are target nodes, count ranges from 3 to 6.
# the ith element in source is linked to ith element in target
target = [3,4,5,6,3,4,5,6,3,4,5,6]
# the strength of each connection
# 'High' in source (index=0) is connected to 'High' in target (index=3) by 548 lines
value = [548,571,129,76,303,1513,1537,564,189,722,1684,1531]

# colors for links in Sankey; hex colors
color_link = ['#EBBAB5','#FEF3C7','#A6E3D7','#CBB4D5', # peach, sand, sea green and light purple
             '#EBBAB5', '#FEF3C7','#A6E3D7','#CBB4D5',
             '#EBBAB5', '#FEF3C7','#A6E3D7','#CBB4D5'] # repeated (4 different target nodes) * (3 start nodes) = 12 nodes

# data to dict, dict to sankey
link = dict(source = source, target = target, value = value, color = color_link) # you can leave the color option but it will
# give greyed out background
node = dict(label = label, pad = 35, thickness = 10) # pad shows the spacings between labels, thickness is the thickness of
# the sankey links
data = go.Sankey(link = link, node = node)

# plot the sankey diagram 
fig = go.Figure(data)
fig.update_layout(
    hovermode = 'x',
    title = "Customer migration from campaign pre to post",
    font = dict(size = 10, color = 'white'),
    paper_bgcolor = '#51504f' # light shade of black (grey black)
    )
fig.show()

# save as png file
plt.savefig("SankeyDiagram.png")

# save as interactive html file
fig.write_html('InteractiveSankey.html')

