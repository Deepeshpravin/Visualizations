# install holoviews 

# import the packages
import holoviews as hv
from holoviews import opts, dim
hv.extension('bokeh')
hv.output(size = 200)

# get the data such that it has three columns - Source, Target and frequency
entities = list(set(data["Source"].unique().tolist() + data["Target"].unique().tolist()))
entities_dataset = hv.Dataset(pd.DataFrame(entities, columns=["Items"]))

# plot the chord diagram
chord = hv.Chord((data, entities_dataset)).select(value=(5, None))
chord.opts(
    opts.Chord(height = 400, width = 400, fontsize = {'labels':'100%'}, cmap='Category20', edge_cmap='Category20', edge_color=dim('Source').str(),
               labels='Items', node_color=dim('Items').str()))
chord.opts(label_text_font_size='9pt')
chord.opts(title = 'Mutual occurrences between X and Y in the given data')

# save the plot as an html file
hv.save(chord, 'filename.html')