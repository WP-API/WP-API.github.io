---
title: WP REST API (v1) Documentation - deprecated
layout: internals
---

Release Process
===============

Time to cook up a new release? Here's the recipe for the baker.

1. Bump the version in the code (key parts are the plugin header, and version
constant, but grepping is the best way to find them all)

2. Generate the changelog! This is the most painful part of release, since we
need a useful changelog. Here's how:

   1. Run [this script][script] to generate the Markdown.

   2. Change each item to match the following format:

      ```
      - Short feature summary.

        Further long-text information can go here. The summary/description
        split is basically the same as phpDoc formatting. Like phpDoc, not
        every commit needs a long description.

        (props @author, [#179][gh-179], [#240][gh-240])
      ```

      This description is either hand-written, or copied from the PR/issue
      description.

   3. Reorder the changelog items to match how important they are. Major
   changes at the top, then other changes further down.

3. Commit the changelog, then tag the release on GitHub and push the tag.

4. Copy the codebase to the plugin's SVN `trunk/` directory.

5. Update the `readme.txt` file with changelog **and** any changes from
the `README.MD file`. Bump the version number and review the `readme.txt`
file for any other needed changes as a result of this release.

6. Commit the new release changes in `trunk`.

7. Test the release, and review the [plugin page](https://wordpress.org/plugins/json-rest-api/) for any process errors.

8. Create a new directory in the SVN `tags/` directory with the new version
number. Copy the files from the SVN `trunk/` directory into the new `tags/x.x`
directory.

9. Commit the tagged release changes in `tags/`.

10. Write the release post for the [Make WordPress Core blog][mc]. Include the
top (important) section from the changelog, along with any other pertinent
information.

[script]: https://gist.github.com/rmccue/c95769c01aff2b486073
[mc]: https://make.wordpress.org/core
