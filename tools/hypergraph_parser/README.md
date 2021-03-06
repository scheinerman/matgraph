# `hypergraph_parser`

`hypergraph_parser` is a program to read text files that represent hypergraphs and
convert them into a form that MATLAB can easily read. It reads from the standard
input and writes to the standard output:
```
./hypergraph_parser < text_input_file > two_col_numeric_file
```
Each line of the input file should be of the following form:
```
edge_name vertex1 vertex2 .... vertexN
```
where each token may is delimited by white space. (Exception, a line that begins
with the `#` character is ignored.)

Only the first word on each line is an edge name; all the other name the
vertices contained in that edge. 

**WARNING**: An edge and a vertex might have the same name, but that does not mean
they are the same thing --- the names of edges have no bearing on the names of
vertices. 

`hypergraph_parser` converts each edge name into consecutive numbers (1, 2, 3,
...) and likewise for vertex names in the order in which they are encountered. 

**WARNING CONTINUED**: If there is a vertex and an edge with the same name, there is
no reason to think they will be given the same number.

See the file `test` for an example of an input file.

The output file is designed for reading into MATLAB with the `load` command.
Each line of this file has two numbers separated by a tab. The first number is
the number assigned to an edge and the second number is the number assigned to a
vertex in that edge. Try `./hypergraph_parser < test` to see what the output looks
like. 

`hypergraph_parser` can also be used for parsing bipartite graph data. In this
case, each line of the input file should be thought of in this form:
```
X-vertex-name Y-vertex-name-1 Y-vertex-name-2 ... Y-vertex-name-N
```

