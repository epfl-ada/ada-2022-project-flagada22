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
    - What are the most important countries according to Wikipedia’s users and how are they connected ?
    - Is this representative of the real geopolitical influence of these countries ?
    - What images of the countries are given by their semantically-close concepts ?

- Who would be the population of the world shaped by Wikispeedia’s users?
    - Who are the most famous people according to Wikipedia’s users ?
    - Would the age, nationality and gender, among others, of these persons, be representative of real world diversity?

## Additional datasets
- **ISO 3166 standard**: this dataset contains a conventional coding to represent the names of countries and of their subdivisions.
- **Wikidata**: this dataset provides structured informations about people and countries that are described in the Wikipedia pages selected in Wikispeedia.

## Methods

Our analysis can be separated into two parts: firstly, seeking information on countries and secondly on people. The methods and approaches followed for the two parts are detailed in the two following subsections.

### Countries
**Gathering information about the continents :** 
In the data at our disposal, we have access to the categories of all the Wikipedia pages of the used subset of Wikipedia. From there, we can extract the categories that correspond to countries and continents and make statistics about continents, such as the number of countries in each continent.

**Finding the most important countries according to Wikipedia's users :** We use *Graph analysis and centrality*. Indeed, we have from the Wikispeedia's dataset the finished and unfinished paths between Wikipedia source and target pages. The latter can be seen as a graph. In particular, we construct a graph where the nodes are the Wikipedia's articles and an edge between two nodes exists if there is a path in the Wikispeedia's dataset where a link between the two articles exists. The weight of the edges correspond to the number of times the two articles are linked in the paths. Python package such as `networkx` package allows to create this graph and use tools of graph analysis. Once this graph constructed from the paths, the importance of a Wikipedia article is determined by its centrality in the graph(more precisely its closeness centrality). We find the most important countries by measuring the closeness centrality of each Wikipedia article related to countries, and by selecting the countries with the higher centrality. The weights of the edges between the nodes of two countries will determine the strength of the connection between those countries.

**Finding information about the countries themselves :** To get more information on the countries (population, area...) we use Wikidata. With the help of `pywikibot`, one searches the wikidata identifier of the Wikipedia webpage of interest and retrieve the wanted information from their wikidata id (e.g. P21 is sex or gender).

**Finding the most important continents :** We use the same method as for the countries. Since there is no Wikipedia page for the continents, the centrality is set to the mean centrality of its countries (the list of the countries in each continent is constructed in the first part). To enable a critical comparison, the centrality of the countries/continents is compared with information on the countries/continent themselves (e.g. population), obtained in the precedent step from Wikidata.

**Finding what concepts/words are the closest to the countries :** For this task, we will use the concept of *Semantic Distance*. The latter quantifies the notion of concepts proximity and is a non-symmetric metric that is created from the links Wikispeedia users make while trying to reach their target Wikipedia page. The distance we create is inspired from the paper [*Wikispeedia: An Online Game for Inferring Semantic Distances between Concepts* of R.West, J.Pineau & D.Precup (2009)](http://infolab.stanford.edu/~west1/pubs/West-Pineau-Precup_IJCAI-09.pdf). Once this distance defined, we simply apply it to countries to find the concepts/articles that are the closest (in terms of semantic distance) to countries.

### People

**Finding the most important people :** We use the graph analysis and closeness centrality of the Wikipedia's articles related to the people, and sort them by centrality to retrieve the most important ones. The method is identical as the one used to determine the most important countries.

**Gathering information on their category :** As before for the countries, we have access the the categories of the Wikipedia's articles. The latter provide information on the category of the people in our dataset. We combine some of the categories to limit their number and to get more global categories. 

**Gathering more information on the people (Age, Gender, Nationality, Religion):** We tried to extract the wanted informations from the plaintext of the articles, and from the html page using `Beautiful soup`, but both approaches have proven to be ineffective. We therefore use Wikidata, as before for the countries, to get these informations using `pywikibot`.

## Timeline

*Up to 02.12.2022:* Focus on homework 2.

*2-9.12.2022:* Extract informations on people and countries from Wikidata, Statistical description of all features of person. (Killian)

*2-9.12.2022:* Finish the maps/visualization for countries and people. (Manon)

*2-9.12.2022:* Finish the implementation of the semantic distance, and apply it to different concepts (e.g. Countries, People). Create the wordclouds. (Zoé)

*2-9.12.2022:* Start working on the website, first designs, first tests. Start writing. (Flore)

*9-16.12.2022:* Last corrections of the code, imagine & create all plots for the datastory, brainstorming on the organization of the datastory. (Everybody)

*16-23.12.2022:* Write and finalize the datastory, comments on the code. (Everybody)

## Organization within the team

**Manon**: Creation of the graph, graph analysis and centrality, application to different sub-questions (e.g. Countries influence, links between countries, people). Creation of the visual content for the parts on countries and people.

**Zoé**: Implementation of the semantic distance, application to countries, creation of the wordclouds.

**Killian**: Extracting information from Wikidata, Statistics of countries and people data. Final analysis of how gender, nationality and age are distributed. Use Wikidata to complete the information panel on Wikipedia pages. Creation of the visual content for the part on people.

**Flore**:  First analyses, Statistics of countries, continents and people data. Web interface modelization.

**Everybody**: Datastory writing.
