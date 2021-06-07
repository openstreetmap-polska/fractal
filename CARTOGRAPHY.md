
# Design goals and guidelines for this style

This is an attempt to outline the goals of this style and the principles under
which the maintainers make decisions. These rules are not set in stone, they
can change and they may not be followed in all cases but contributors should
be able to expect that they are generally the guiding principles design wise.

It does not make much sense to try following these principles blindly as a
contributor without understanding them, they are meant to guide you to develop
an intuition and understanding how to make design decisions to fit into the
overall concept of this style.

## General purpose

This style is a feedback mechanism for mappers to validate their edits. There 
are multiple needs in OSM community, so it tries to fulfill as many of them as 
possible. Micromapping is underrepresented in current styles, so Fractal tries
to make it as important as more traditional cartography.

## Main goals

The following goals need to be balanced against each other to serve the purposes
above. There is no fixed order of priorities. Apart from these goals there are
of course also technical constraints and requirements that need to be taken into
account.

* **Legibility and clarity** - The map should be intuitively readable by users with some general experience using maps without a map key, preferrably with relatively little effort. A map key or more extensive experience using this map style can be required for clearly identifying minor differences or the exact meaning of certain features but in broad strokes orientation and identification of map elements should be possible on an intuitive level. We also aim for the map appearance to be esthetically pleasing.
* **Being understandable and supportive for mappers** - To serve as feedback for mappers and encourage correct mapping this style needs to render the data in a way that allows mappers to understand how the data produces a certain rendering result based on basic observation without in depth understanding how map rendering works or looking at the style implementation. Lack of visual context can be as much of a problem (lack of clues for specific shapes and placement) as showing too much elements (like underground platforms or cables). The rule of the thumb is to show what's visible on the ground.
* **Diversity** - The style should represent the diversity of the OSM community and geography in general. The most obvious element to serve this goal is showing the local names everywhere on earth in their respective scripts. This goal however goes beyond labels. Both physical and cultural geography differs a lot globally and the aim is to represent this variety. This also means the target map user is the potential global map user and no special consideration is given to the current geographic distribution of actual map use.
* **A rich map** - This style deliberately creating a fairly rich map showing a significant number of different features. This way it shows the richness of OSM data and gives a broad recognition to the mappers' work. It also prevents so called "taging for rendering" (tagging as different object just to see the changes on the map). The aim is not however to show all or even most of the OSM data.
* **Maintainability** - The implementation of this style should not be too hard to maintain. This refers to complexity of the code and how fast the style can be parsed when rendering it, which is important for efficient development work. Complexity and fragile interdependencies should be avoided.
* **Adaptability and ease of use** - The style should be easy to customize, like for creating localized or special purpose maps. It is also important to keep demands on rendering infrastructure for serving the style low so it is not too difficult and costly to set up a tile server for this style or a specialized variant of it.
* **Scalability** - Different objects belong to different scales: bigger ones should be visible earlier, smaller ones should be visible later. This helps to avoid cluttering map with details. Size is the most common and objective feature that we can use instead of subjective choices based on what's important. However importance might be used as a secondary rule when needed.
