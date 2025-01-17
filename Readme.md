[![RimWorld Alpha undefined](https://img.shields.io/badge/RimWorld-Alpha%20undefined-brightgreen.svg)](http://rimworldgame.com/)

A better research tree.

# Features
 - automatically generated to maximize readability*. 
 - shows research projects, buildings, plants and recipes unlocked by each research project.
 - projects can be queued, and colonists will automatically start the next project when the current research project completes.
 - search functionality to quickly find research projects.

# FAQ
*Can I add/remove this from an existing save?*
You can add it to existing saves without problems. Removing this mod will lead to some errors when loading, but these should not affect gameplay - and will go away after saving.

*Why is research X in position Y?*
Honestly, I have no idea. The placement of projects (nodes) is automated to minimize the number of crossings between dependancies (edges), and reduce the total length of these edges. There are many possible scenarios in which this can lead to placements that may appear non-optimal. Sometimes they really are non-optimal, sometimes they just appear to be so. See also the *technical* section below for more information.

*Can I use this with mod X*
Most likely, yes. Added researches and their requirements are automatically parsed and the tree layout will be updated accordingly. ResearchPal implements a lot of the same functionality as this mod, and the research queue will likely not work correctly if both mods are loaded.

*This looks very similar to ResearchPal*
Yep. ResearchPal is based on a legacy version of this mod that was kept up-to-date by SkyArkAngel in the HCSK modpack. I haven't worked on this mod in a long time, but I recently had some spare time and decided to give it another go. Feel free to use whichever you like better (ResearchPal has an entirely different layout algorithm). You can run both mods side by side to check out the different tree layouts, but be aware that the research queue will not work correctly if both mods are loaded.

# Known Issues
 - The vertical labels for tech levels are drawn in the wrong location when UI scale is not 1. This is a known problem for me, the same issue appears in my Work Tab mod. As soon as I have a working solution, I'll go and fix it.
 - Layouts are not perfect, if you have experience with graph layouts - please do feel free to look at the source code, and/or implement a Sugiyama layout algorithm for me that runs in C# .NET 3.5 (Mono 2.0).

# Technical
So how does this all work?

Creating an optimal layout is a known problem in the area of *Graph Theory*. There's serious mathematicians who've spent years of their live trying to figure out this problem, and numerous solutions exist. The group of solutions most relevant to our research tree (a *directed acyclic graph*, or *DAG*) is that derived from Sugiyama's work. Generally speaking, these algorithms have four steps;
 - layering (set the *x* coordinates of nodes, enforcing that follow-up research is always at a higher x position than any of its prerequisites, this is a fairly straightforward heuristic)
 - crossing reduction (set the *y* coordinates of nodes such that there is a minimal amount of intersections of connections between nodes)
 - edge length reduction (set the *y* coordinates of nodes such that the length of connections between nodes is minimal)
 - horizontal alignment (set the *y* coordinates of nodes such that the connections between nodes are straight as much as possible)

The final step is the hardest, but also the most important to create a visually pleasing tree. Sadly, I've been unable to implement two of the most well known algorithms for this purpose; 
 - Brandes, U., & Köpf, B. (2001, September). Fast and simple horizontal coordinate assignment.
 - Eiglsperger M., Siebenhaller M., Kaufmann M. (2005) An Efficient Implementation of Sugiyama’s Algorithm for Layered Graph Drawing.
Luckily, the crossing reduction and edge length reduction steps partially achieve the goals of the final step. The final graph is not as pretty as it could be, but it's still pretty good - in most scenarios. 



# Contributors
 - Templarr:	Russian translation
 - Temp:	
 - Suh. Junmin:	Korean translation
 - rw-chaos:	German translation
 - 53N4:	Spanish translation

# Think you found a bug? 
Please read [this guide](http://steamcommunity.com/sharedfiles/filedetails/?id=725234314) before creating a bug report,
 and then create a bug report [here](https://github.com/FluffierThanThou/ResearchTree/issues)

# Older versions
All current and past versions of this mod can be downloaded from [GitHub](https://github.com/FluffierThanThou/ResearchTree/releases).

# License
All original code in this mod is licensed under the [MIT license](https://opensource.org/licenses/MIT). Do what you want, but give me credit. 
All original content (e.g. text, imagery, sounds) in this mod is licensed under the [CC-BY-SA 4.0 license](http://creativecommons.org/licenses/by-sa/4.0/).

Parts of the code in this mod, and some content may be licensed by their original authors. If this is the case, the original author & license will either be given in the source code, or be in a LICENSE file next to the content. Please do not decompile my mods, but use the original source code available on [GitHub](https://github.com/FluffierThanThou/ResearchTree/), so license information in the source code is preserved.

# Are you enjoying my mods?
Show your appreciation by buying me a coffee (or contribute towards a nice single malt).

[![Buy Me a Coffee](http://i.imgur.com/EjWiUwx.gif)](https://ko-fi.com/fluffymods)

# Version
This is version 3.4.494, for RimWorld 1.0.2150.