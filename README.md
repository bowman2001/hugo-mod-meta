# hugo-mod-social

This module generates meta tags for social networks and search engines. Hugo already offers a set of internal templates for this purpose.
- [**Open Graph**](https://gohugo.io/templates/internal/#open-graph) for Facebook and others
- [**Twitter Cards**](https://gohugo.io/templates/internal/#twitter-cards)
- The **Schema** template is undocumented but is using the same concept as the other two templates

These templates are doing fine if we stick to the data parameters and the content organization they expect. They are the starting point for this project.

## Why then this module?

This project became necessary for me, because of three reasons.
1. My image resources are sometimes organized in an incompatible way.
2. My content structure is often different. (Simply: The `.Description` contains a very short description of the content, too short for the description meta tag. I would like the `.Summary` to appear there. But those details won’t matter for this module!) 
3. The Hugo maintainers and core developers don’t find the time to review pull request of the template code. There are a lot of stale PRs which look reasonable—at least to me—but are a waste of time. Hopefully this module provides an alternative, and we don’t have to bother the core maintainers and Go developers with template problems we can solve ourselves.

## How?

The main concept of this module is to make no assumptions about the project structure. The partials for generating the meta tags will call other partials to get the necessary content. These content partials can be replaced by the project or theme maintainers using this module. So the input is completely configurable.

The output obviously doesn’t need any configuration. The resulting `<meta>`-tags need to follow the demands of the providers we like to use. So the results of the provided partials will be completely predictable.
