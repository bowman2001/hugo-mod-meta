# hugo-mod-meta

This module generates the title tag and the usual necessary meta tags for a Hugo site. It also addresses the meta tags for social networks and search engines with opengraph and twitter tags and some schema JSON-LD. Hugo already offers a set of internal templates for this purpose:
- [**Open Graph**](https://gohugo.io/templates/internal/#open-graph) for Facebook and others
- [**Twitter Cards**](https://gohugo.io/templates/internal/#twitter-cards)
- The **Schema** template is undocumented but is using the same concept as the other two templates

The Hugo templates are doing fine if we stick to the data parameters and the content organization they expect. They are the starting point for this project.

## Why this new module then?

This project became necessary for me because of four reasons:
1. My image resources are often organized in a way these partials can’t find them.
2. My content structure is a little different than what these templates expect. (Simply: The `.Description` contains a very short description of the content, too short for the description meta tag. I would always like the `.Summary` to appear there. But those details don’t matter for this module!) 
3. The Hugo maintainers and core developers don’t have the time to review pull requests for template code. There are many stale PRs for Hugo which look reasonable—at least to me—but have been a waste of time. Hopefully this module provides an alternative, and we don’t have to bother the core maintainers and Go developers with template problems we can solve ourselves.
4. Reusability: I don’t want to think about meta tags more than absolutely necessary and will include this module in every project of mine. From reading old discussions between active developers I get the impression that others also reinvent the generation of these tags repeatedly in their projects. 

## How?

The main concept of this module is to make **no assumptions about the project structure and configuration**. The partials for generating the meta tags will call other partials to get the necessary content. These content partials can be replaced by the project or theme maintainers using this module. Therefore, the way they retrieve the necessary data is completely configurable. 

There are some default templates to start with, but to assure the correct input is up to everyone using this module by providing the partials fitting their content structure.  

The output obviously doesn’t need any configuration. The resulting `<meta>`-tags need to follow the demands of the providers we like to use. So the correct results of the provided partials are predictable. They should adapt in time to any changes of the specifications by the social network providers.  

## Specifications 

- Twitter: <https://developer.twitter.com/en/docs/twitter-for-websites/cards/overview/markup> 

### Twitter
A lot of tags are possible, lets start with the most important ones:
- Title allows max 70 characters.
- Description allows max 200 characters.
- Image (one) needs to be a WEBP, JPEG, PNG or a GIF. No SVG and animated GIF won’t animate.

## Testing
The social network or search engine providers offer validation tools.
