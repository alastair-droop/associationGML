# Generate graphML from Association Data

The `makeGML` script converts association files into valid [graphML](http://graphml.graphdrawing.org) data.

## Association File format

Association files are designed to be a simple method of capturing associations between elements. The association format is:

~~~
A:B,C
D:
~~~

In the above example, the node `A` is associated with nodes `B` and `C`. The node `D` is not associated with any other nodes.

## `makeGML` Usage

~~~
usage: makeGML [-h] [-v] [-r] [-a GRAPH_NAME] [-p NODE_PREFIX] <file>

Convert association text file to GraphML format

positional arguments:
  <file>                input association file

optional arguments:
  -h, --help            show this help message and exit
  -v, --version         show program's version number and exit
  -r, --allow-reciprocal
                        allow reciprocal edges
  -a GRAPH_NAME, --graph-name GRAPH_NAME
                        graph name
  -p NODE_PREFIX, --node-prefix NODE_PREFIX
                        node prefix string
~~~

## Example Output

The small example file above yields the following graphML:

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<graphml xmlns="http://graphml.graphdrawing.org/xmlns"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://graphml.graphdrawing.org/xmlns
  http://graphml.graphdrawing.org/xmlns/1.0/graphml.xsd">
  <graph id="G" edgedefault="undirected">
    <node id="A" />
    <node id="B" />
    <node id="C" />
    <node id="D" />
    <edge source="A" target="B" />
    <edge source="A" target="C" />
  </graph>
</graphml>
~~~