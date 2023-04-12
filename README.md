# hugo-mod-meta

This module generates the title, many meta tags and and JSON+LD schema scripts for [Hugo](https://gohugo.io) pages. These are processed by search engines and social networks to create some kind of preview on their pages.

Hugo already offers a set of internal templates for this purpose:
- [**Open Graph**](https://gohugo.io/templates/internal/#open-graph) for Facebook and others
- [**Twitter Cards**](https://gohugo.io/templates/internal/#twitter-cards)
- The **Schema** template is undocumented but is using the same concept as the other two templates

The Hugo templates are doing fine as long as we stick to the data parameters and the content organization they expect. They were the starting point for this project.

## Why this new module then?

This project became necessary out of four reasons:
1. My resources are organized in a way the internal Hugo partials can’t find them.
2. My content structure is different from what these templates expect. (Simple example: The `.Description` only contains a very short description of the content for navigation links which is too short for the description meta tag. I like to use a dedicated SEO description or at least a `.Summary` with one or two full sentences to appear there.) 
3. The Hugo maintainers and core developers are stretched thin and don’t find the time to review pull requests for internal template code. There are many stale PRs for these templates with reasonable small improvements. This module should provide an alternative, because I don’t want to bother the Hugo maintainers with template problems I can write myself.
4. Reusability: I don’t want to think about meta tags more than absolutely necessary and will include this module in every project of mine. From reading discussions between other developers I get the impression they also reinvented the generation of these tags repeatedly in their projects. The overhead of using a configurable module should pay off fast.

## How?

The main concept of this module is to make **no fixed assumptions about the project structure**. The partials for generating the meta tags call other partials to get the necessary content. These content partials can be replaced in every project to fit its structure. 

But we don’t have to write all those partials from scratch. There are default templates to start with, which resemble the internal Hugo way.  

The output doesn’t need a lot of configuration. The resulting tags and schema scripts need to follow the demands of the internet services we like to address. The correct results of the provided partials are predictable. They should adapt in time to any changes of the specifications by social network and search providers.  

## Specifications 

- Twitter: <https://developer.twitter.com/en/docs/twitter-for-websites/cards/overview/markup> 
- Opengraph: <https://ogp.me/>
- Schema (JSON-LD): <https://developers.google.com/search/docs/advanced/structured-data/search-gallery>

## Testing
The social network or search engine providers offer validation tools.
TODO: Add links

## Alternatives
[SEO module by the New Dynamic](https://github.com/theNewDynamic/hugo-module-tnd-seo)
