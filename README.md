# hugo-mod-social

This module generates meta tags for social networks and search engines. Hugo already offers a set of internal templates for this purpose:
- [**Open Graph**](https://gohugo.io/templates/internal/#open-graph) for Facebook and others
- [**Twitter Cards**](https://gohugo.io/templates/internal/#twitter-cards)
- The **Schema** template is undocumented but is using the same concept as the other two templates

These templates are doing fine if we stick to the data parameters and the content organization they expect. They are the starting point for this project.

## Why this module, then?

This project became necessary out of four reasons:
1. My image resources are sometimes organized in a way, that these partials can’t find them.
2. My content structure is often different. (Simply: The `.Description` contains a very short description of the content, too short for the description meta tag. I would always like the `.Summary` to appear there. But those details won’t matter for this module!) 
3. The Hugo maintainers and core developers don’t have the time to review pull requests for template code. There are many stale PRs for Hugo which look reasonable—at least to me—but are a waste of time. Hopefully this module provides an alternative, and we don’t have to bother the core maintainers and Go developers with template problems we can solve ourselves.
4. Reusability: I don’t want to think about meta tags more than absolutely necessary and will include this module in every project of mine. From reading old discussions between active developers I get the impression that others also reinvent the generation of these tags repeatedly in their projects. As soon as this project gets some helpful contributions I will happily remove my name as the license holder and replace it with "contributors" or something, so everybody can rely on its future development. 

## How?

The main concept of this module is to make **no assumptions about the project structure and configuration**. The partials for generating the meta tags will call other partials to get the necessary content. These content partials can be replaced by the project or theme maintainers using this module. Therefore, the way they retrieve the necessary data is completely configurable. 

Therefore, this module won’t extract the necessary data from a project necessarily by itself. There will be some default templates to start with, but to assure the correct data collection is still up to every project maintainer by providing the partials fitting their content structure.  

The output obviously doesn’t need any configuration. The resulting `<meta>`-tags need to follow the demands of the providers we like to use. So the correct results of the provided partials are predictable. They should adapt in time to any changes of the specifications by the social network providers.  

## Specicications 

- Twitter: <https://developer.twitter.com/en/docs/twitter-for-websites/cards/overview/markup> 

### Twitter
A lot of tags are possible, lets start with the most important ones:
- Title allows max 70 characters.
- Description allows max 200 characters.
- Image (one) needs to be a WEBP, JPEG, PNG or a GIF. No SVG and animated GIF won’t animate.

## Testing
The social network or search engine providers offer validation tools. In the folder `validate` is a Hugo project which produces all tags for some test content and configuration. It needs to pass all validation engines. At the moment I don’t now if its possible to automate the validation free of charge.
