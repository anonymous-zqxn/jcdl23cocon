# CoCon

A data set capturing the combined use of research artifacts, contextualized through academic publication text.

* [Data sample](#data) (`data/`)
* [Code](#usage) (`contexthraph/`)

## Usage

### NetworkX

The methods described below can be imported from `contextgraph.util.graph`.  
You’ll also want to `import networkx as nx` in your code.

##### load\_full\_graph()

Returns the full graph in which all nodes and edges types.

parameter | values | default | explanation
--------- | ------ | ------- | -----------
shallow   | bool   | False   | True: all node and edge features except for type will be discarded.
&zwnj;    | &zwnj; | &zwnj;  | False: nodes and edges have features according to the data available on Papers with Code.
directed  | bool   | True    | True: Return the graph as an nx.DiGraph.
&zwnj;    | &zwnj; | &zwnj;  | False: Return the graph as an nx.Graph.
directed  | bool   | True    | True: Return the graph as an nx.DiGraph (for an overview of directions of edges see `_load_edge_tuples` in `contextgraph/util/graph.py`).
&zwnj;    | &zwnj; | &zwnj;  | False: Return the graph as an nx.Graph.
with\_contexts  | bool | False | True: Also load “context” nodes (each appearance of a used entity in a paper results in a context node connected as entity--part\_of-&gt;context--part\_of-&gt;paper). **Be aware** that this will result in *a lot* of additional nodes.
&zwnj;    | &zwnj; | &zwnj;  | False: Don’t load context nodes.

##### load\_entity\_combi\_graph()

Load graph only containing the entity nodes connected by edges which represent their co-occurrence papers based on a *scheme* setting described below. (**NOTE**: to access edge attributes later, G.edges(data=True) has to be used!)

parameter | values | default | explanation
--------- | ------ | ------- | -----------
scheme    | {'weight', 'sequence'} | 'sequence' | 'sequence': edges have two properties (1) `linker_sequence` (a list of the co-occurrence paper IDs) and (2) `interaction_sequence` (a list of integers to be understood as “time steps”. Each integer value is the `<month>` in which a co-occurrence paper is published. The month in which the very first co-occurrence paper within the returned graph is published in month 0).
&zwnj;    | &zwnj; | &zwnj;  | 'weight': edges have a weight attribute that denotes the number of co-occurrence papers that exist between the two entities.

### PyTorch Geometric

The methods described below can be imported from `contextgraph.util.torch`.

##### load\_entity\_combi\_graph()

Load graph only containing the entity nodes connected by edges which represent their co-occurrence papers. Edge weights represent the number of co-occurrence papers.


## Preprocessing

* Set paths in `contexthraph/config.py`
* Run `$ python3 preprocess.py`
