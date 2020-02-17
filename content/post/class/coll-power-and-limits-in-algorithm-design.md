---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Colloquium: Power and Limits in Algorithm Design"
subtitle: ""
summary: ""
authors: [admin]
tags: [colloquium, graph-theory, algorithms]
categories: [class]
date: 2020-02-14T11:13:37-06:00
lastmod: 2020-02-14T11:13:37-06:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---
## Structures in Algorithm Design: Power and Limits
Talk by [Hung Le](https://hunglvosu.github.io/)

[Similar to talk](https://etd.ohiolink.edu/!etd.send_file?accession=kent1397345185&disposition=inline)

### Distance Sparsification in Bounded Geometry

#### Bounded Geometry
{{% alert note %}}
*Bounded Geometry*  
Doubling space for peer-to-peer networks.
{{% /alert %}}
Finite metric space. identificiation, symmetry, triangle inequality.  

Doubling dimension. Think of metric space as edge-weighted graph (by distance).  
[Doubling Spaces](https://en.wikipedia.org/wiki/Doubling_space)

#### Distance Sparsification
[Sparsification](https://www.cs.utah.edu/~jeffp/teaching/cs5140-S16/cs5140/L25-GSparse.pdf)  

Question: Trade-off between stretch and lightness.  

### Application of Spanners
* Routing
* ML
* Distributed Systems

#### Construct Minimum Spanning Tree
[Kruskal algorithm](https://www.geeksforgeeks.org/kruskals-minimum-spanning-tree-algorithm-greedy-algo-2/)
Add t stretch factor for the determination of adding edge. Simple adjustment to algorithm.  


Question: What is the sparsity of the algorithm.  

General graph

#### Improvement
Steiner Euclidean dimension. Steiner pointer = points not in the original set. Reduces the weight, but always has more edges than MST. Reduces sparsity quadratically.

### Combinatorial Optimization
1. Traveling Salesperson Problem
2. Local Search

#### Bounded clique minor
Graphs that can be drawn without edge crossing  
Tree-like graphs

#### Subset TSP
Shortest tour in a subset of the weighted graph (can use other points not in the target subset).  

Approximation
* [Christofides' algorithm](https://en.wikipedia.org/wiki/Christofides_algorithm) in poly time

#### Light Preservers
* Nearly optimal
* Light

Lift solution from light solution to the original graph.

#### Local Search

#### Sublinear Separation

### Future Work
* Simple/Practical Algorithms, specifically sublinear separation
* Does local search work for all local problems?  
Ex: Fails for weighted problem
* Embed into tree-like graphs
* The key is to closed under submatrices
