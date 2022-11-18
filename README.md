# Wikiworld: the world created by wiki users

## Abstract

With more than 6 million English articles, Wikipedia can be seen as the world's largest and most-read reference work in history. The platform proposes a quick and easy way to navigate between this mass of information through the usage of hyperlinks connecting different articles. How users of Wikipedia use these links give a real insight into the cultural connections that exist between diverse concepts. The Wikispeedia dataset provides even more information in that direction, by providing link paths made by players attempting to join two different concepts. These connection paths between articles thus exhibiting connections in the player’s imagination of these concepts. This connectivity graph allows us to construct a representation of Wikispeedia users reality, described through the centrality of countries, peoples and historical events. Our project aims at observing this vision of the world, and questioning the existing differences with our real world.

## Research Questions

The main question that will drive our dataset analysis and representation is:

<p align="center">
<strong>If the world was shaped by Wikispeedia’s users, how would it be?</strong>
</p>

Around this guiding inquiry, we will try to answer the following subquestions:

- What countries will constitute the world shaped by Wikispeedia’s users?
    - What are the most important countries according to Wikipedia’s users ?
    - Is this representative of the real geopolitical influence of these countries ?
    - What images of the countries are given by their semantically-close concepts ?

- Who would be the population of the world shaped by Wikispeedia’s users?
    - Who are the most famous people according to Wikipedia’s users ?
    - Would the age, nationality and gender, among others, of these persons, be representative of real world diversity?

- What would be the main historical events in the history of this world ?
    - What are the most important historical events for Wikipedia’s users?

## Additional datasets
- **ISO 3166 standard**: this dataset contains a conventional coding to represent the names of countries and of their subdivisions.
- **Wikidata**: this dataset provides structured informations about people and countries that are described in the Wikipedia pages selected in Wikispeedia.

## Methods
**Graph analysis and centrality**
The finished and unfinished paths between Wikipedia source and target pages can be seen as a graph. Python package such as `networkx` package allows to analize the dataset as a graph and use tools of graph analysis (measure the centrality of each article (i.e. node) to determine its importance, find clusters...)

**Semantic distance**
Concepts proximity is quantified by the semantic distance, a non-symmetric metric that is created from the links Wikispeedia users make while trying to reach their target Wikipedia page. This distance is inspired from the paper [*Wikispeedia: An Online Game for Inferring Semantic Distances between Concepts* of R.West, J.Pineau & D.Precup (2009)](http://infolab.stanford.edu/~west1/pubs/West-Pineau-Precup_IJCAI-09.pdf).

**People and countries informations**
Defining characteristics of people and countries are extracted from the information box of their Wikipedia page using Beautiful soup. Further data is obtained from the associated Wikidata dataset.


## Timeline

*Up to 02.12.2022:* Focus on homework 2

*09.12.2022:* Statistical description of all features of person, country datasets and of graph and semantic distance representations. Add information obtained from Wikidata. Compare findings with other 100 most famous people datasets. (Flore & Killian)

*2-9.12.2022:* Finish the maps/visualization for History and Countries (Manon)

*2-9.12.2022:* Apply the semantic distance tool implemented to different concepts (e.g. Countries, People) (Zoé)

*9-16.12.2022:* Last corrections of the code, imagine & create all plots for the datastory, brainstorming on the organization of the datastory

*16.12.2022:* Write datastory

*23.12.2022:* Finalize the datastory

## Organization within the team

**Manon**: Data analysis with graphs, application to different sub-questions (e.g. Countries influence, People).

**Zoé**: Semantic distance analysis.

**Flore, Killian**: Statistics of countries and people data. Final analysis of how gender, nationality and age are distributed. Use Wikidata to complete the information panel on Wikipedia pages.

**Everybody**: Datastory writing and web interface modelization.

## Question for the TAs

- What value to use for the Dirichlet parameter in the semantic distance approach?
- Do you have a suggestion on the best way to access and handle the data from Wikidata? A specific library? 
- In order to represent (visualize) the importance of the countries, we would like to transform our choropleth map into a cartogram. Do you have any idea how to do this? (Do you maybe have the name of a python library we could use?)

