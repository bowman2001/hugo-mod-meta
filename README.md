# hugo-mod-meta

This module generates the title tag and the usual necessary meta tags for a Hugo site. It also addresses the meta tags for social networks and search engines with opengraph and twitter tags and some schema JSON-LD. Hugo already offers a set of internal templates for this purpose:
- [**Open Graph**](https://gohugo.io/templates/internal/#open-graph) for Facebook and others
- [**Twitter Cards**](https://gohugo.io/templates/internal/#twitter-cards)
- The **Schema** template is undocumented but is using the same concept as the other two templates

The Hugo templates are doing fine if we stick to the data parameters and the content organization they expect. They are the starting point for this project.

## Why this new module then?

This project became necessary for me because of four reasons:
1. My image resources are often organized in a way these partials can’t find them.
2. My content structure is a little different than what these templates expect. (Simply: The `.Description` only contains a very short description of the content for navigation links which is too short for the description meta tag. I always like the `.Summary` with one or two full sentences to appear there.) 
3. The Hugo maintainers and core developers are stretched thin and don’t find the time to review pull requests for template code. There are many stale PRs for the internal templates with reasonable small improvements. This module could provide an alternative and we don’t have to bother the Hugo maintainers and Go developers with template problems we can solve ourselves.
4. Reusability: I don’t want to think about meta tags more than absolutely necessary and will include this module in every project of mine. From reading discussions between other developers I get the impression they also reinvented the generation of these tags repeatedly in their projects. The overhead of using a configurable module should pay off fast while using the module for similar structured projects.

## How?

The main concept of this module is to make **no assumptions about the project structure and configuration**. The partials for generating the meta tags call other partials to get the necessary content. These content partials can be replaced by the maintainers. The way this module gets the necessary data is completely configurable. 

You don’t have to write partials for the input from scratch, there are some default templates to start with. But they may not suit your content structure and to assure the correct input is up to every maintainer using this module.  

The output obviously doesn’t need a lot of configuration. The resulting `<meta>`-tags need to follow the demands of the providers we like to address. The correct results of the provided partials are predictable. They should adapt in time to any changes of the specifications by social network and search providers.  

## Specifications 

- Twitter: <https://developer.twitter.com/en/docs/twitter-for-websites/cards/overview/markup> 
- Opengraph: <https://ogp.me/>
- Schema (JSON-LD): <https://developers.google.com/search/docs/advanced/structured-data/search-gallery>

### Twitter
Lets start with the most important tags:
- Title allows max 70 characters.
- Description allows max 200 characters.
- Image (one) needs to be a WEBP, JPEG, PNG or a GIF. No SVG and animated GIF won’t animate.

### Opengraph

### Schema

## Testing
The social network or search engine providers offer validation tools.
