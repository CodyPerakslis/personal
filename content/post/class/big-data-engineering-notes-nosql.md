---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Big Data Engineering Notes: NoSQL"
subtitle: ""
summary: ""
authors: [admin]
tags: [data-engineering,csci5751]
categories: [class]
date: 2020-02-12T18:27:29-06:00
lastmod: 2020-02-12T18:27:29-06:00
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
# {{< staticref "files/notes/05_storage_and_serialization.pdf" >}}Storage and Serialization{{% /staticref %}}
## Data Modeling
**Important section**.  
Every abstraction hides a complexity of the layer below. Our modeling will need to go to the lowest layer possible to find the best optimization.  

### Impedance Mismatch
The disconnect between models of two layers.  
### Locality
Fewer seeks/joins and compression options, but more memory used (disk and main).  

{{% alert note %}}
The answer to any specific question, like what is the right level of denormalization, is "depends on the business question."
{{% /alert %}}

## Schema
Just how you describe the shape of your data.  

A table is just a translation layer over files. So the best way to optimize a table is to optimize how the files are stored.  

**Schemas do change**. Make sure to follow good schema evolution rules.  

### Hash Index
\#1 Thing: Avoid storage hotspots (everything hashing to the same values)  
### Bloom Filters
Even with a high rate of false positives, searching much less of the data can be powerful

### Storage Orientation
First effective optimization
* Row-oriented: When you often query most/all the columns
* Column-oriented: When often query subset of columns (analytics)

{{% alert note %}}
*Data Analytics Lifecycle*: Often stores Hi-Fi data as row-oriented, then writes analytic data as column-oriented for Low-Fi data.
{{% /alert %}}

# Deliverable
Story conveyed in the story. The appendix allows to dig deeper.  
Make it look good, pictures are nice.  
Appendix not required, but often used for information overflow.  

# {{< staticref "files/notes/06_NoSQL_Storage_KVDB_DocDB.pdf" >}}NoSQL Data Modeling{{% /staticref %}}

## Data Model Design
*Purpose*: Describe to other people, because they need to know how to use it.  
Final project include data model. List/Pictures \>\>\> Paragraphs.  

### Keys
Delimit attributes by entity types (SSN vs customer id)  
