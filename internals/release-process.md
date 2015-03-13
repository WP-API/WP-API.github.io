---
title: WP REST API Documentation
layout: internals
---

Release Process
===============

Time to cook up a new release? Here's the recipe for the baker.

1. Bump the version in the code (key parts are the plugin header, and version constant, but grepping is the best way to find them all)

2. Generate the changelog! This is the most painful part of release, since we need a useful changelog. Here's how:

   1. Run [this script](https://gist.github.com/rmccue/c95769c01aff2b486073) to generate the Markdown.

   2. Change each item to match the following format:

      ```
      - Short feature summary

        Further long-text information can go here. The summary/description split
        is basically the same as phpDoc formatting. Like phpDoc, not every commit
        needs a long description

        (props @author, [#179][gh-179], [#240][gh-240])
      ```

      This description is either hand-written, or copied from the PR/issue description.

   3. Reorder the changelog items to match how important they are. Major changes at the top, then other changes further down.

3. Commit the changelog, then tag the release on GitHub and push the tag.

4. Copy the codebase to the plugin's SVN directory, then copy the changelog into the readme.txt there. Also ensure you version bump here.

5. Commit readme/changes to trunk, then create new tag from that.

6. Write the release post, including the top (important) section from the changelog, along with any other important information.

