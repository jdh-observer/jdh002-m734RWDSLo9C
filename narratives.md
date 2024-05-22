---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.16.1
  kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
---

<!-- #region citation-manager={"citations": {"": []}} tags=["title"] -->
# imagineRio Narratives: A Storytelling Tool for Spatial History in Rio de Janeiro
<!-- #endregion -->

<!-- #region tags=["contributor"] -->
### Bruno  Buccalon [![orcid](https://orcid.org/sites/default/files/images/orcid_16x16.png)](https://orcid.org/0000-0002-6463-936X) 
Rice University
<!-- #endregion -->

<!-- #region tags=["contributor"] -->
 ### Alida C.  Metcalf [![orcid](https://orcid.org/sites/default/files/images/orcid_16x16.png)](https://orcid.org/0000-0001-8175-8339) 
Rice University
<!-- #endregion -->

<!-- #region tags=["contributor"] -->
### David  Heyman [![orcid](https://orcid.org/sites/default/files/images/orcid_16x16.png)](https://orcid.org/0000-0003-2727-5111) 
Axis Maps
<!-- #endregion -->

<!-- #region tags=["copyright"] -->
[![cc-by-nc-nd](https://licensebuttons.net/l/by-nc-nd/4.0/88x31.png)](https://creativecommons.org/licenses/by-nc-nd/4.0/) 
© Bruno Buccalon, Alida C. Metcalf, and David Heyman. Published by De Gruyter in cooperation with the University of Luxembourg Centre for Contemporary and Digital History. This is an Open Access article distributed under the terms of the [Creative Commons Attribution License CC-BY-NC-ND](https://creativecommons.org/licenses/by-nc-nd/4.0/)

<!-- #endregion -->

<!-- #region tags=["disclaimer"] -->
An earlier version of this paper was presented at the Social Science History Association Annual Meeting in Philadelphia, November 12, 2021.
<!-- #endregion -->

<!-- #region tags=["keywords"] -->
Rio de Janeiro, Urban History, Spatial History, Map-based Storytelling, Scrollytelling, Historical GIS, HGIS
<!-- #endregion -->

<!-- #region tags=["abstract"] -->
This paper introduces [_imagineRio Narratives_](https://narratives.imaginerio.org/), a map-based storytelling tool designed for scholars, students, and dedicated amateurs interested in the spatial history of the city of Rio de Janeiro. Our tool allows users to write spatial narratives integrated with the historical mapping platform [_imagineRio_](https://imaginerio.org/), offering a user-friendly editor that does not require expertise in Geographic Information Systems (GIS). In this paper, the _narrative_ layer discusses the idea behind the project, our previous experience using ESRI StoryMaps, and three case studies on narratives created by users. The _hermeneutics_ layer presents the scholarly debates and technical choices shaping our design, a guided tour of key functionalities, and details on the development process. We conclude by sharing our vision for _imagineRio_ as an inclusive platform that fosters open research and scholarship.
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
## Introduction
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
Rio de Janeiro is a city of the global south that struggles with inequality but that revels in its rich history. Founded by the Portuguese crown in 1565 to claim the Guanabara Bay, the city of Rio began as a military camp below the tall granite peak known today as the _Pão de Açúcar_ (Sugar Loaf). The city center soon moved to the top of the hill further inside the bay where Brazil’s governor built an acropolis. Only a few written sentences describe this settlement; there are no surviving maps, plans, sketches, or painted views. Later however, as the residents moved down and began to lay out streets that paralleled the harbor, maps and sketches capture the seventeenth-century port city that, by the eighteenth, became one of the richest in the Atlantic World. It was also one of the most unequal. Tens of thousands of slaves landed in Rio yearly, most enroute to plantations and mines inland, but some remaining behind. At the turn of the nineteenth century, aproximately 47 percent of Rio's residents were enslaved (<cite data-cite="7748027/C6Q3NJHF"></cite>:60, <cite data-cite="7748027/E4NNMKER"></cite>:129). In the following decades, approximately 900,000 enslaved persons disembarked in the city coming mostly from port cities located in West and West-Central Africa, a figure that represents about 24% of all trafficked population during the first half of the nineteenth century (<cite data-cite="7748027/CNCDVWQ5"></cite>).
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
Glimpses of the city are captured in texts, maps, and imagery that date from the time when the royal court, fleeing Napoleon, arrived in 1808. Throughout the nineteenth century, visitors recorded impressions in letters, sketches, water colors, providing representations of the city and its residents. Rio became the capital of independent Brazil in 1822, but the slave trade continued until 1850 and slavery was not abolished until 1888. After the fall of the empire in 1889, the city underwent major urban reforms, many of which were visually documented. A wealth of imagery by Brazilian artists, photographers, and writers allows the history of the city’s changes to be followed in the twentieth century. Over time, Rio’s natural environment, urban fabric, and self-representation has changed dramatically, and there are infinite stories to be written, mapped, and illustrated.
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
Today Rio extends over 1,200.329 km2 and its population is estimated at 6.7 million (<cite data-cite="7748027/XCBHE7FE"></cite>). Its neighborhoods are densely populated, whether located on the original city site, the hillside communities known as favelas, the suburbs, or the beachfront communities along the Atlantic coast, which are popular destinations for tourists. Rio remains a cultural hot spot in Brazil, not only because of its music and iconic carnival celebration but also for its universities, museums, archives, and libraries hosting foundational documentation for Brazilian history. Yet it continues to be shaped by the historical legacies of colonialism and slavery. The city is often described as dual: the city of the asphalt—the formal city with paved streets, apartment buildings, and functioning public services—and the city of the hills—the informal, self-made communities that lack reliable access to basic public services. While favelas have been widely studied and continue to host approximatetly one fifth of Rio residents, the mapping of its territories remains a challege to this day (<cite data-cite="7748027/3YNMATP6"></cite>, <cite data-cite="7748027/G7DF4X4C"></cite>).
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
Two scholarly endeavors are foundational to the study of spatial history in Rio de Janeiro. First, the scholarship of geographer Mauricio de Abreu, who operated in the intersection of urban studies and historical geography, influencing many students and researchers in Brazil (<cite data-cite="7748027/5CY7295B"></cite>, <cite data-cite="7748027/P5HMPBST"></cite>). Second, the experimental work of Richard White, Zephyr Frank, and Erik Steiner, who established the Spatial History Project at Stanford University (<cite data-cite="7748027/SIE9GRW3"></cite>, <cite data-cite="7748027/2KZHP4VZ"></cite>). Frank's project _Terrains of Memory_ produced detailed spatial analysis of Rio during the second half of the nineteenth century, focusing on social and economic issues that could be investigated and presented through interactive data visualizations (<cite data-cite="7748027/B6A6CN2Z"></cite>, <cite data-cite="7748027/GA9V2UW6"></cite>). While Abreu considered his interest in Rio's history as something more specific than urban studies or city history, Frank framed spatial history as a methodology that relied on visualization as a research strategy (<cite data-cite="7748027/3ZTRGFB7"></cite>, <cite data-cite="7748027/ZMMHPMES"></cite>). Although operating within a similar research agenda, neither Abreu or Frank produced data visualizations of how the urban spaces of Rio de Janeiro changed over a large period of time.
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
_imagineRio_ is a historical mapping platform about the city of Rio de Janeiro, focused on its visual representations. At the heart of _imagineRio_ stands an interactive map, accurate to the year, that cartographically represents the city's physical spaces from the 16th century to the present. Supported by a spatial database and an image library, the platform offers creative ways to study the past through historical maps, urban plans, and artistic views. Its user interface enables visual documents to be queried in time and space through an interactive timeline, illustrating the city as it existed and as it was imagined. Launched in 2015, the project is the result of a collaboration between professors Alida C. Metcalf and Farès el-Dahdah at Rice University and cartographer David Heyman at digital studio Axis Maps (<cite data-cite="7748027/JQXTIMIU"></cite>).
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
First conceived as a physical exhibition that would bring together historical maps, urban plans, and artistic views, _imagineRio_ quickly grew into a digital platform. The co-PIs were attracted to Historical GIS (HGIS) because it could capture with thick, descriptive, and visual detail how the city existed, and how it was imagined, over time (<cite data-cite="7748027/DDWAMIME"></cite>:124-144). This approach fits within a common framework among historians applying GIS tools "to visualize past landscapes and the changing morphology of built environments over time”, being particularly fruitful for urban studies (<cite data-cite="7748027/7EBR95YN"></cite>:8,12). Most HGIS projects prefer to focus on “key dates”, covering detailed spatial patterns at a relatively short span of time, and having historical maps as their focal point (<cite data-cite="7748027/S49GF7EU"></cite>). _imagineRio_'s geographic database covers more than five centuries and nearly 100 historical maps are available to its users. Urban plans by architects, urbanists, and engineers hold many clues to understanding how and why the city changed over time; forty-eight are georeferenced so the city can be seen as it was imagined (and often how it came to be built). The  spatial data of _imagineRio_ was harvested from georeferenced historical maps, with vector features drawn over satellite imagery to minimize distortion. Each geographic feature is associated with a first and last year, and changes can be visualized using a filter activated by a time slider.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
Although GIS software is designed to be precise and accurate, humanists known that the past is fuzzy and subject to different and often conflicting interpretations. Yet, our HGIS approach strives to render a city representation at any one year in time that is essential for Rio, since its landscape has undergone tremendous changes with the pulling down of hills, the draining of swamps, and the expansion of the city, through land reclamation, over what was formerly water. Locating artistic views of the city in time and space (such as sketches, watercolors, paintings, and photographs) also helps to identify patterns of visual representation, contextualizing artistic works within a unique digital urban environment. This image-based approach can be complemented by other HGIS projects that undertake quantitative historical analysis, such as the analysis of census data to illustrate residential patterns (<cite data-cite="7748027/TXBTTXGZ"></cite>), the spatial analysis of mortality by race, disease, and age (<cite data-cite="7748027/6PHSDRRB"></cite>), or the establishment of historical address locators (<cite data-cite="7748027/AX68488Q"></cite>).
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
In 2021, _imagineRio_ released a new version designed to bridge the usability gap between image collections and mapping applications. This version introduced a side-by-side user interface that gives equal attention to the spatial and image-based functionalities, greatly expanding the number of georeferenced photographs available to the public. Among these images, the work of many Brazilian photographers such as Marc Ferrez, Georges Leuzinger, and Guilherme Santos became searchable spatially and temporally for the first time. It also introduced major technical improvements, such as a faster mapping engine, a microservices architecture, and compliance with the International Interoperability Image Framework (IIIF). The improvements were elaborated in collaboration with the Instituto Moreira Salles (IMS) in Brazil, and received funding from the Getty Foundation Digital Art History initiative (<cite data-cite="7748027/K99SFGKZ"></cite>).
<!-- #endregion -->

```python tags=["figure-imaginerio-*"]
from IPython.display import Image, display
metadata={
    "jdh":{
        "module": "object",
        "object": {
          "type": "image",
          "source": [
            "Display of georeferenced photographs in _imagineRio_ \(2022\)."
          ]
        }
    }
}
display(Image("media/imaginerio-v3.png", width=1000), metadata=metadata)
```

<!-- #region tags=["narrative"] -->
Offering a user-friendly interface to browse visual documents through space and time, _imagineRio_ presents georeferenced information as a simplified web-based Historical Geographic Information System (HGIS). Streets, parks, public spaces, neighborhoods, and landscapes can be visualized on an interactive basemap, along with georeferenced historical maps and artistic representations of specific regions in the city. The new version also expands the search capabilities of the image library, which now has a dedicated panel on the left side of the screen. Within it, users can search and filter results over the map panel, located on the right side of the screen. This integration opens up new research dimensions for scholars interested in change over time, urban photography, architectural design, urban planning, and environmental history.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
As with most web-based projects, the history of _imagineRio_'s software development is closely tied to how browsers, web standards, and libraries shape technical possibilities and user interface conventions. During its initial years, the main technical challenge of the project was the styling and rendering of a large geographical dataset using raster tiles, a rendering technology that required basemaps to be processed year-by-year using a custom server. The resulting experience was that, for each year selected in the timeline, the user had to wait for the square tiles to load. In 2021, with the adoption of a new mapping engine that relies on vector tiles as a rendering solution, the graphical computation was transfered from the server to the client. This allowed the geographical data curated by Rice's Spatial Studies Lab to load instantly to the user.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
To adapt to similar changes in the future, _imagineRio_ adopted a microservices architecture, with self-contained applications for data wrangling, search, and front-end client. Among these is a serverless image repository compliant to the IIIF specifications. The image metadata processing was also redesigned, with a Extract-Transform-Load (ETL) pipeline reconciling entities with Wikidata to offer multilanguage labels in English and Portuguese. The project is open source and [published on Github](https://github.com/imaginerio/) under a MIT License.
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
The craft of visual arguments in spatial history is both a practical and theoretical challenge (<cite data-cite="7748027/J95BKNCX"></cite>). As with any map, abstraction and selection shape its production, and maps only work because they simplify the world. Most geographical data from _imagineRio_ comes from the georeferencing and vectorization of historical maps, which can be problematic, as some were produced under a colonial mindset in which "cartographic silence becomes an affirmative ideological act" (<cite data-cite="7748027/QBGIYSGH"></cite>:70). To ensure that the platform does not oversimplify critical aspects of the city's history, we use these maps to create a digital cartographic representation, organized in different layers that can be revised and improved. The sources we use come from a variety of libraries and archives, such as the Biblioteca Nacional (Brazil), the Arquivo Nacional (Brazil), the Arquivo Geral da Cidade do Rio de Janeiro (Brazil), the Library of Congress (USA), the Arquivo Historico Ultramarino (Portugal), and others. Although the resulting layers (streets, buildings, squares, land use, etc.) were built from many maps, gaps and omissions remain. Neighborhoods outside of the central city are only superficially mapped over time, leaving the history of these areas and residents largely silent. Similarly, _imagineRio_ does not include the larger environmental context of the Guanabara Bay, as it falls outside of the city's limits. These are issues that can be addressed over time, as we develop communities of users interested in contributing to the mapping of the city.
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
Another issue affecting the project is that its interactive features cannot be successfully integrated into scholarly publications. Traditional academic journals only offer black and white illustrations, which hardly do justice to interactive visualizations (<cite data-cite="7748027/I8MXG7G7"></cite>). Born-digital journals offer scholars the opportunity to include color illustrations and zoomable maps, making specialized journals attractive venues (<cite data-cite="7748027/UCTNTPWP"></cite>). Academic platforms like Cambridge Core offer similar digital enhancements, thereby bringing research developed on digital platforms into well-established academic journals (<cite data-cite="7748027/6WQZ4WEP"></cite>). Yet, the end result is a PDF file, which often is hidden behind a subscrition paywall. For instance, the Laboratory of Urban Analysis and Digital Representation at the Federal University of  Rio de Janeiro (Laurd/UFRJ) has created several 3D models of _Morro do Castelo_ representing its demolition, but they can only be seen in academic publications in 2D (<cite data-cite="7748027/UMZNRLXU"></cite>). Similarly, most users of _imagineRio_ who wish to include an illustration drawn from their research simply take a screenshot of the interactive map in a certain year (<cite data-cite="7748027/QXEBGIUE"></cite>). In exceptional cases, scholars have created argument-driven maps using the layers of _imagineRio_ with the help of a GIS specialist. Such maps appears in the doctoral theses of historians Antonio Higino da Silva and Higor Figueira Ferreira (<cite data-cite="7748027/UXXDQJ5H"></cite>, <cite data-cite="7748027/8VUMRXGC"></cite>).
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
Customized maps do an excellent job of visualizing historical arguments, for they display data drawn from the interests, sources, and research questions of their authors. However, most scholars do not have access to GIS specialists, and even when they do, the final results often lack in terms of the expressive cartography present in _imagineRio_. Static visual representations are useful to give spatial context to historical arguments, but they do not convey to the reader the experience of interacting with layers of geographic and temporal information. Considering these limitations, how could the interactive features of _imagineRio_ be better integrated into scholarly publications? How could its users contribute data to the platform in the context of their own research? And how could we promote community engagement around Rio's spatial history, online and on the ground? To address these questions, we first experimented with map-based storytelling before settling on creating our own tool.
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
## Storytelling with Maps
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
Central to the user experience of _imagineRio_ is the ability to zoom to a specific area, to select a date, to highlight layers, and to see the map respond accordingly. We became interested in bringing these interactive elements so that our users could write their own narratives, using _imagineRio_ as a basemap. To address the limitations of scholarly publications, we began experimenting with ESRI map-based storytelling products, which offered ways to incorporate maps, images, and text in an interactive, online publication. In 2018, we crafted our first bilingual story map about the remainings of the _Carioca_ aqueduct in Rio (<cite data-cite="7748027/BWT4U6F9"></cite>). After that, through ESRI's various templates, such as Cascade and Map Journal, we experimented with ways to combine maps, text, and imagery. To test these possibilities, we reached out to two senior scholars of Rio de Janeiro, Mary Karasch and Sandra Lauderdale Graham, and proposed the creation of story maps that would weave together their research and _imagineRio_ with the goal of reaching a broader, online audience.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
In the past decade, map-based visual storytelling became an important mode of readership engagement, offering hybrid user experiences with significant impact in fields such as data journalism. (<cite data-cite="7748027/SJPTC295"></cite>, <cite data-cite="7748027/HUKRSVSA"></cite>). John Branch's Snow Fall piece, published by _The New York Times_ in 2012, was particularly impactful in expanding the range of possibilities for web-based multimedia storytelling (<cite data-cite="7748027/7D9TWK8N"></cite>). The rise of interactive narratives subsequently led to open-source projects that harnessed their integration with maps, such as the _Odyssey.js_ project (<cite data-cite="7748027/V7RAX78K"></cite>). Often promoted as showcases of mapping companies, most tools rely on a technique known as _scrollytelling_, in which a webpage animates in reaction to the scrolling of the mouse (<cite data-cite="7748027/6DJ8WI93"></cite>,<cite data-cite="7748027/E8DJN7VC"></cite>,<cite data-cite="7748027/SIHII7JJ"></cite>). In our case, we decided to start exploring ESRI products by relying on an institutional subscription from our university. ESRI's storytelling solutions have been renamed and relaunched as different products many times, with the most recent being the StoryMaps (<cite data-cite="7748027/E7HAPHQ3"></cite>). 
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
In the story map _“Rio de Janeiro: A Colonial City until 1850”_ by historian Mary Karasch, we selected the Story Map Journal template for an argument intended to unfold chronologically. Because the template features two parallel windows, readers could engage simultaneously with Karasch’s written text, on the left, and with _imagineRio_, on the right. Accompanied by images selected by Karasch, the story map allowed readers to easily accompany the changes in the city over time, and to see them spatially. Readers may enter _imagineRio_ through an iframe and freely explore its features, zooming in and out, moving around, and selecting georeferenced maps and geolocated images to view. Returning to Karash’s illustrated text in the left window, readers may enlarge images in order to see greater detail. Karasch’s text resembles an academic article–it has footnotes and endnotes (not supported in the original template), an argument, and it follows the scholarly writing conventions used by historians. This story map, available in both English and Portuguese, resulted in an authoritative text that is interactive, heavily illustrated, and spatially specific (<cite data-cite="7748027/AFWF3GAD"></cite>).
<!-- #endregion -->

```python tags=["figure-karasch-*"]
from IPython.display import Image, display
metadata={
    "jdh":{
        "module": "object",
        "object": {
          "type": "image",
          "source": [
            "Karasch's story map has _imagineRio_ embedded as an iframe."
          ]
        }
    }
}
display(Image("media/storymap-karasch.png", width=1000), metadata=metadata)
```

<!-- #region tags=["narrative"] -->
In the story map _“Henriqueta’s Day on the Streets, Rio de Janeiro, 1850s”_ by historian Sandra Lauderdale Graham, we selected the Story Map Cascade template for a thematic and focused argument on how an African streetseller moved through the city on a typical day. In this story, the text scrolls over images and georeferenced historical maps, which were custom labeled and highlighted to illustrate specific places. These images appear in various sizes, from full screen to small size, with linked citations that take readers to their respective archival collections. At the end of the story, readers are invited to _imagineRio_ to explore the city in the 1850s. This story map does not have lengthly academic footnotes or endnotes, but it ends with a detailed narrative on the sources used to reconstruct Henriqueta’s daily movements, including specific archival references. Also bilingual, its Portuguese version was adopted as an assigned reading by several history professors in Rio, after the COVID-19 pandemic shuttered classrooms (<cite data-cite="7748027/2WFGXFT4"></cite>).
<!-- #endregion -->

```python tags=["figure-graham-*"]
from IPython.display import Image, display
metadata={
    "jdh":{
        "module": "object",
        "object": {
          "type": "image",
          "source": [
            "Lauderdale Graham's story map uses custom labels to illustrate its spatial context."
          ]
        }
    }
}
display(Image("media/storymap-graham.jpg", width=1000), metadata=metadata)
```

<!-- #region tags=["narrative"] -->
Drawing from these previous experiences, in the 2020 spring semester, we decided to use story maps for an assignment in a History of Brazil undergraduate course. Students had to pick a theme from the novel _Memórias de um Sargento de Milícias_ (1852) by Manuel Antônio de Almeida, to research their chosen theme in academic publications, and to create a narrative about life in Rio during that moment in time. The original goal was for each student to create an independent story map, whereas in previous years, students had created posters or slide presentations. However, with the outbreak of Covid-19, we decided to ask students to contribute to one, collaborative story map. The instructor was responsible for a substantial part of the writing, and each student contributed an independent section. Each section had a map, created by a GIS specialist, which helped the students to annotated their own information. These annotations were displayed over the _imagineRio_ basemap, so that spaces described in the text could be visualized. The resulting story map is titled _“Rio de Janeiro in the Time of the King”_ and was also translated into Portuguese (<cite data-cite="7748027/TPG6SDD2"></cite>).

<!-- #endregion -->

```python tags=["figure-students-*"]
from IPython.display import Image, display
metadata={
    "jdh":{
        "module": "object",
        "object": {
          "type": "image",
          "source": [
            "The story map created with Rice students uses _imagineRio_'s raster tiles."
          ]
        }
    }
}
display(Image("media/storymap-students.png", width=1000), metadata=metadata)
```

<!-- #region tags=["narrative"] -->
Both Karasch and Lauderdale Graham’s story maps are rich interactive publications that bring academic research to broader audiences. Nevertheless, each took months to create. Scholars mostly dedicated to print, these guest authors found working outside of traditional workflows difficult. In Karasch's case, the author focused on the text and the selection of historical images to illustrate it, while a team created the story map. This team included a GIS specialist, a historian familiar with _imagineRio_, and an editorial assistant. In Graham’s case, the story map evolved into a co-authored project with Metcalf, who created and exported custom maps from ArcGIS. With the students, ESRI products seem ideal for teaching tech-savvy individuals, allowing them to work intensively with historical images and maps. Particularly with students who cannot read Portuguese, the use of visual documents helps them to engage with the assignment in sophisticated ways. Nevertheless, it was clear that a GIS specialist was needed to create the interactive maps. In addition to the instructor, two specialists were involved in the project: one set up accounts and taught the students the platform, while the other created the basemaps from _imagineRio_ that each student annotated.
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
Although ESRI storytelling products have been widely adopted, our experience working with students and scholars to create story maps with _imagineRio_ data revealed several limitations. Despite the well-designed editor, the various StoryMaps products required writers to rely on GIS specialists to fully develop the mapping component of their stories. All of the story maps we created required consultation, both for learning the editor and creating the maps. Technically, the integration with _imagineRio_'s geographical data felt either as a workaround (iframe) or of limited interactive functionality (raster tiles). Moreover, ESRI products require a paid subscription. These limitations convinced us that proprietary tools were out of reach for most of our audience, since many of our intended users are in Brazil and are unlikely to have access to institutional or financial support. Therefore, we developed our own open-source solution to address these limitations.
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
## Building a tool
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
We conceived _imagineRio Narratives_ as a map-based storytelling tool designed for scholars, students, and dedicated amateurs interested in the spatial history of the city of Rio de Janeiro. Our main goal was to create a writing tool for spatial narratives that would be simple to use, bilingual, and without the need for GIS expertise. We wanted to give access to the geographical layers and georeferenced maps of _imagineRio_, which makes it easy for any user to visualize change over time. More than merely encouraging the sharing of research materials, we were inspired by how the production of history could benefit from an open-source attitude towards argument-driven digital history (<cite data-cite="7748027/GU27KZDX"></cite>, <cite data-cite="7748027/WII44YH7"></cite>). Considering that many regions and groups of the city were erased from historical maps and silenced from archival sources, we needed a way for users to elaborate and to annotate their own spatial information. The writing of Rio’s spatial history had to be open to new voices and perspectives, especially from groups not fully represented in its official historical record.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
Regarding project management, our aim was to develop a storytelling tool that could leverage the full potential of vector tiles and adhere to the best practices in interactive cartography design. The project comprised of three stages. During Stage One (February to August 2020), we conceptualized and developed an initial prototype. During Stage Two (September 2020 to August 2021), we established a user group in Rio de Janeiro to create narratives and provide feedback. Finally, during Stage Three (March 2022 to March 2023), we completed bilingual translations and conducted specialized workshops with teachers in Rio. Funding for these stages was provided by grants from Rice University’s Humanities Research Center, through its Spatial Humanities Initiative, which is supported by the Andrew W. Mellon Foundation, and the Ken Kennedy Institute.
<!-- #endregion -->

<!-- #region tags=["hermeneutics"] -->
As for software development, _imagineRio Narratives_ is a web application that utilizes KeystoneJS, an open-source Content Management System (CMS) with a MongoDB database. The NextJS framework was used to create the user interface, which accounts for roughly 80% of the total development effort. The front-end interacts with the database via a GraphQL API. To enhance functionality, the application is integrated with _imagineRio_'s microservices architecture that incorporates the diachronic atlas map renderer, the MapboxGL basemap styles, and the imaginerioSearch library to retrieve information on geographical features and basemaps. The application's data model is structured around projects, which consist of ordered sets of cards. Each card stores customization variables and metadata related to the map orientation. All data is organized hierarchically under user profiles, allowing users to export their personal data as JSON files at any time. The data contained in a sample project reads as follows:
<!-- #endregion -->

```python tags=["hermeneutics"]
{
  "User": {
    "name": "Warren Dean",
    "email": "wdean@nyu.edu",
    "projects": [
      {
        "title": "With Broadax and Firebrand",
        "description": "The Destruction of the Brazilian Atlantic Forest",
        "tags": [
          {
            "name": "Atlantic Forest"
          },
          {
            "name": "Environmental History"
          }
        ],
        "category": "History",
        "imageTitle": "Featured Image",
        "source": "https://www.example.com/",
        "url": "https://cnd.imaginerio.org/image-1.jpg",
        "cards": [
          {
            "title": "Title of the card",
            "description": "Description of the card",
            "order": 1,
            "size": "Medium",
            "year": 1818,
            "longitude": -43.18914483352785,
            "latitude": -22.896216487308735,
            "zoom": 16.20517641780579,
            "bearing": 175.87998354956002,
            "pitch": 32.482914224253186,
            "selectedFeature": "null",
            "layers": [],
            "basemap": {
              "ssid": "2589170",
              "title": "Planta da Cidade do S. Sebasti\u00e3o do Rio de Janeiro",
              "firstYear": 1817,
              "lastYear": 1821,
              "longitude": -43.1810763343022,
              "latitude": -22.9010009606826,
              "creator": "Souto, P. S. F."
            },
            "opacity": 1,
            "media": "null",
            "imageTitle": "Sample Image",
            "source": "https://www.example.com/",
            "url": "https://cnd.imaginerio.org/image-1.jpg",
            "annotations": [
              {
                "feature": "{\"type\":\"Feature\",\"properties\":{\"title\":\"Parque do Mendanha\"},\"geometry\":{\"type\":\"Point\",\"coordinates\":[-43.456000046961684,-22.84524094246816]},\"id\":\"62145f786d1ade00567ca229\"}"
              }
            ]
          }
        ]
      }
    ]
  }
}
```

<!-- #region tags=["narrative"] -->
### Gallery
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
The gallery is the entry point, where users can explore the narratives that have been published by other users. There, each published narrative is linked to its own detail page, which presents information such as the author's name, title, and description. Additionally, the detail page features images that are relevant to the story, helping to provide context and visual aids to the reader. The homepage features a carefully curated selection of narratives, with the most recent publications listed first. These narratives are categorized by themes, such as history, architecture, or literature, and can be further filtered using tags provided by the author. The categories and tags provide a useful means for users to explore narratives that are relevant to their interests, whether they are seeking to learn more about a particular topic or simply looking for an engaging story to read.
<!-- #endregion -->

```python tags=["figure-gallery-*"]
from IPython.display import Image, display
metadata={
    "jdh":{
        "module": "object",
        "object": {
          "type": "image",
          "source": [
            "The gallery of _imagineRio Narratives_."
          ]
        }
    }
}
display(Image("media/narratives-gallery.png", width=1000), metadata=metadata)
```

<!-- #region tags=["hermeneutics"] -->
We are currently exploring different ways to operate the gallery and considering various options that would best serve our users. One option is to have an open gallery that allows anyone to publish their narrative. In this case, we would periodically review the published narratives and showcase those that we find to be particularly interesting or noteworthy, designating them as "Editor's Picks." Another potential option is to implement a simplified peer-review process where narratives would be sent to an editorial board for evaluation. If approved, these narratives would receive a stamp of peer-review, which would be useful for academic purposes as _imagineRio Narratives_ could serve as a form of scholarly publishing. Lastly, we are considering offering personal galleries linked to user profiles, which would allow authors to publish their work without impacting the main gallery. We recognize that some users may prefer to use our tool for annotating their spatial research rather than writing publishable narratives, and we aim to provide a platform that caters to all types of users.
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
### Viewer
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
After selecting a narrative, the user will be redirected to the viewer interface. In this interface, the contents of the narrative are structured in a series of cards that are displayed alongside the interactive map. The use of cards encourages users to be brief and to divide long texts into shorter sections, which can include images with captions or audiovisual content. Each card is linked to a specific geographic position and orientation in _imagineRio_. As users scroll through the narrative, the application determines the location of the next card and sends its information to the mapping engine. The mapping engine then animates the transition between the geographic coordinates of the current card and the next one. This approach ensures that the user has a smooth and seamless experience as they navigate through the narrative.
<!-- #endregion -->

```python tags=["figure-videojuliana-*"]
from IPython.display import HTML, display
metadata={
    "jdh":{
        "module": "object",
        "object": {
          "type": "video",
          "source": [
            "Short video of the narrative viewer."
          ]
        }
    }
}
display(HTML('<iframe width="640" height="400" src="https://www.youtube-nocookie.com/embed/8qdSeuBhy8E?controls=0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>'), metadata=metadata)
```

<!-- #region tags=["narrative"] -->
### Editor
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
The editor is the authoring environment for users who want to create their own narratives. It allows images to be uploaded onto cards with different dimensions, such as small, medium, or fullscreen. Additionally, image captions and links to can be added directly to the card. Users can also use georeferenced maps from _imagineRio_ within the editor, enabling them to easily incorporate historical maps and other geospatial data into their narratives. Although users cannot import georeferenced iconography for now, they can upload their own research images to illustrate their arguments. The editor also supports embedded media from external providers such as YouTube, Vimeo, and Soundcloud. In the map window, users can annotate and label geographic features using points, lines, and polygons, highlighting specific places and events relevant to their arguments. For example, a writer documenting changes in a neighborhood can drop points on the map and add labels that make it clear where the locations described lie. Furthermore, users can manipulate the annotated map by tilting, panning, rotating, or zooming in at any time for a better view.
<!-- #endregion -->

```python tags=["figure-editor-*"]
from IPython.display import Image, display
metadata={
    "jdh":{
        "module": "object",
        "object": {
          "type": "image",
          "source": [
            "The editor of _imagineRio Narratives_."
          ]
        }
    }
}
display(Image("media/narratives-editor.png", width=1000), metadata=metadata)
```

<!-- #region tags=["hermeneutics"] -->
We took inspiration from popular slideshow applications, such as PowerPoint and Google Slides, as well as writing tools like Scrivener, when designing the editor interface. Our goal was to break down content into small chunks, making it easy for users to organize their thoughts, images, and writing. We decided to use the term "card" instead of "slide" as it was a more fitting frame of reference for users entering into an unfamiliar medium, such as our map-based storytelling tool. To begin creating a narrative, users need to create a project with basic information like a title and description. Once in the editor, the next step is to create a new card, which will be listed on the left sidebar. The middle section of the editor has a simple text editor with formatting options like bold and italics, as well as a superscript font that users can use to manually insert footnotes. Below the text box, there are customization options that allow users to adjust the size of the card or add external media. On the right side of the editor, users will find the map window where they can select the year in the timeline and the geographic position of their interest.
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
## Building a community
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
The spatial history of any city is doomed to incompletion if not thought as a collective task, which required specific strategies for community engagement. Our approach on that front is to promote user-generated content and to embrace user requests based on real-world use cases. We want to promote a co-design process informed by engaged users, from which we can improve our platform (<cite data-cite="7748027/KNF8W7S8"></cite>). Our first outreach initiative happened between December 2020 and July 2021, when our team hosted a series of online workshops with a group of fifteen researchers, students, and scholars based in Rio de Janeiro. These participants were selected based on their knowledge and lived experiences in the city, as well as their interest in _imagineRio_. Each participant was given their own account and agreed to draft a narrative on a topic of their choice. Our participants included historians, architects, urban planners, social scientists, and educators, and each received a honorarium for their contributions.
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
The first goal of our user group was to give feedback on the user interface and functionalities of our tool, to test its usability, and to offer suggestions on how to improve it. In order to collect feedback in a structured way, we created an [online forum](https://forum.imaginerio.org/) for users to present themselves, report bugs and request new features. Since we could not honor all requests, we had to select those that seemed most impactful. The forum interaction was key for nurturing a collaborative mindset among participants and for identifying critical issues that needed to be addressed before the public launch. Although active during the group dynamic, forum participation declined after a few months, proving harder to maintain without dedicated community management. We also developed a legal framework to allow user-generated content in _imagineRio_. Lawyers in Brazil and at Rice University crafted a bilingual [Terms of Use](https://www.imaginerio.org/en/terms) and a [Privacy Policy](https://www.imaginerio.org/en/privacy) that added a layer of protection to our users, while giving us ways to remove any instance of hate speech. These documents also guarantee that users could download their personal data and delete their accounts.
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
Our second goal was to foster community engagement in Rio, empowering users who could serve as ambassadors for our project. This process continued with the public launch of user accounts, which became available for anyone after we concluded the user group meetings. In 2022, together with professor Deborah Fontenelle, who participated in our user group, we started a training program for teachers in Rio. To inspire creative ways to use _imagineRio Narratives_ in Portuguese-speaking classrooms, Fontenelle conducted a series of in-person workshops to assess the use of our tool in high schools and undegraduate programs. Finally, to gather this growing community, we hosted the first in-person _imagineRio_ seminar at the Instituto Moreira Salles, in November 2022.
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
## Case Studies
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
As of May 2024, _imagineRio Narratives_ has 140 users, who have created 114 projects, using 268 images, and 1143 annotations. From this pool of projects, we select three case studies to illustrate the diverse range of applications for our tool in exploring aspects of the city's spatial history. The first case study focuses on a novel. The second case study examines an urban reform. The third case study discusses the history of favelas. Through these examples, we hope to demonstrate how our tool facilitates new ways of understanding the history of Rio de Janeiro, and how a diverse group of users decided to make use of these possibilities.
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
In "_Agosto de Rubem Fonseca: uma leitura espacial e imagética_" by sociologist Juliana Marques, the narrative takes the reader back to the political crisis that led to the tragic suicide of President Getúlo Vargas in 1954. Marques uses historical photographs, creating a powerful connection between the spaces of the city and the writings of novelist Rubem Fonseca. Adopting two narrative voices: that of Fonseca (in italics) and her own (in light bold), Marques links events with fiction and shows both in the city’s spaces. The reader sees exactly where the key events unfolded in the city, and by using photographs from before and after the event, the reader becomes aware of how the city is changing and remaining the same. A YouTube video imbedded in the Narrative allows the reader to watch a specific clip with the basemap set to the year and location where the events took place (<cite data-cite="7748027/82IQJH68"></cite>).
<!-- #endregion -->

```python tags=["figure-casejuliana-*"]
from IPython.display import Image, display
metadata={
    "jdh":{
        "module": "object",
        "object": {
          "type": "image",
          "source": [
            "A small-size card with embedded image and annotated coordinates over the 1954 _imagineRio_ basemap. Narrativa by Juliana Marques available at https://narratives.imaginerio.org/view/6033f30a66f6f3001879495f"
          ]
        }
    }
}
display(Image("media/case-juliana.jpg", width=1000), metadata=metadata)
```

<!-- #region tags=["narrative"] -->
In "_A Modernização Portuária da Capital Monárquica: A Doca da Alfândega_" by historian Antônio Carlos Higino da Silva, the narrative places on the basemap are labeled so that readers can clearly follow the argument. Interested in documenting how the port of Rio changed, Silva dropped points on the basemap and added labels. The map is thus customized for the reader: not only is it set for the correct time and for the specific spaces in the city being discussed, but the labels allow the reader to easily and clearly see what the text references. This spatial precision enables the writing of histories that are currently unknown, overlooked, invisible, or not deemed significant (<cite data-cite="7748027/62HQVAH9"></cite>). 
<!-- #endregion -->

```python tags=["figure-casehigino-*"]
from IPython.display import Image, display
metadata={
    "jdh":{
        "module": "object",
        "object": {
          "type": "image",
          "source": [
            "A medium-size card with embedded image and annotated coordinates over the 1885 _imagineRio_ basemap. Narrative by Antonio Carlos Higino da Silva available at https://narratives.imaginerio.org/view/600f1696c405e10018988544"
          ]
        }
    }
}
display(Image("media/case-higino.jpg", width=1000), metadata=metadata)
```

<!-- #region tags=["narrative"] -->
In "_Favelas cariocas_" by architect Maria Helena Salomon, the narrative discusses the history of central city slums (_cortiços_) and the later emergence of hillside communities (_favelas_), which are carefully contextualized in time and space. Salomon begins with the specific areas of the city where swamps were filled in the early nineteenth century. By setting the time slider on the basemap to a specific year and by zooming to the desired location, the author shows and the reader sees exactly when and where change is occurring. Moreover, by selecting a georeferenced map, Salomon encourages the reader to engage directly with a cartographic primary source and to visually comprehend how the space was represented at the time of her analysis (<cite data-cite="7748027/DJM2S2R7"></cite>).
<!-- #endregion -->

```python tags=["figure-casemariahelena-*"]
from IPython.display import Image, display
metadata={
    "jdh":{
        "module": "object",
        "object": {
          "type": "image",
          "source": [
            "A small-size card with embedded image and annotated coordinates over a georeferenced 1941 map from the Library of Congress. Narrative by Maria Helena Salomon available at https://narratives.imaginerio.org/view/6064c5acf2a23d0018282c15"
          ]
        }
    }
}
display(Image("media/case-mariahelena.jpg", width=1000), metadata=metadata)
```

<!-- #region tags=["narrative"] -->
## Conclusion
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
_imaginerio Narratives_ marks a turning point in our community outreach, for we recognized the need to empower and engage meaningfully with our users in Rio de Janeiro by offering inclusive ways for sharing their own perspectives. This is particularly critical considering the erasures of historical maps that shape our platform, and the active role that we must have in addressing its shortcomings. Our bilingual storytelling tool allow users to create, label, and annotate any location of the city represented in _imagineRio_, and to embed custom media objects like images, audio and video. In addition, the accompanying online forum offers an open channel for users to share their feedback, and to communicate with and learn from each other. We can now offer many more scholars, students, and dedicated amateurs an writing platform for argument-driven spatial history. We hope that our tool can lead to new ways of interpreting the past, understanding the present, and envisioning a better future for Rio.
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
## Acknowledgments
<!-- #endregion -->

<!-- #region tags=["narrative"] -->
The authors are grateful to Bruno Sousa, Livia Tiede, Ludmila de Souza Maia, and Amy Ferguson for their support in the crafting of the story maps discussed in this article. We also thank Farès el-Dahdah and Rice's Spatial Studies Lab for their tremendous support over the years. We appreciate the support of Rice undergraduate Ethan Denson in drafting the English tutorial, Martim Passos in preparing the video animation, Ivan Borges Sales in developing the terms and policies, and Paula Kupfer for editorial suggestions. A special thanks goes to our user group: Antonio Carlos Higino da Silva, Cintia Mechler, Daryle Williams, Deborah Fontenelle, Higor Figueira Ferreira, José Pessoa, Juliana Marques, Keila Grinberg, Leticia Souza, Lise Sedrez, Maria Helena Salomon, Monica Lima, Naylor Vilas Boas, Sergio Burgi, and Verena Andreatta. Finally, at the Journal of Digital History we would like to thank Frédéric Clavert, Andreas Fickers, Elisabeth Guerard, Mirjam Pfeiffer, the special issue editors Maria Eriksson and Pelle Snickars, and the anonymous reviewers for their generous support.
<!-- #endregion -->

<!-- #region tags=["hidden"] -->
## Bibliography
<!-- #endregion -->

<!-- #region tags=["hidden"] -->
<div class="cite2c-biblio"></div>
<!-- #endregion -->
