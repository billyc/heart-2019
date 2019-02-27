# Building an open, web-based data visualization platform for MATSim

# 0. Abstract

# 1. Introduction

MATSim is an open-source framework for implementing large-scale agent-based transport simulations. [x] There are many tools available for analyzing results, both open-source and commercial, and MATSim is widely used for transportation research in academic settings.

# 2. Motivation

A notable gap in those tools, however, is in web-based visualization. As more and more public discourse occurs online, this creates a challenge for using MATSim in public policy settings: the only people who can meaningfully examine and explore results are those with extensive technical knowledge and access to the specialized software and large datasets involved.

## Hypothesis: Web-based platform is now advanced enough to visualize large-scale simulation results without proprietary software, plugins, etc

# 3. Requirements

The research team at TU Berlin had several "blank slate" discussions before any code was written: meaning, if we could start at the very beginning and design something completely web-based and open, what would the bare minimum requirements be for it to be truly useful? The following requirements emerged from those discussions.

## Requirement 1: Web browser-based

Given the above-stated motivation and hypothesis that the modern web platform is ready for large-scale visualization tasks, the most obvious requirement is that the product of this research must work with any modern web browser.

Several specific web technologies developed and made widely available in recent years enable us to perform this research: HTML 5, CSS 3, WebGL, ECMA Script 6, and Web Workers. This paper will not attempt to fully describe these technologies, as our focus is on using them for the task of data visualization, but the brief descriptions below may be helpful:

- **HTML 5** improves and, critically, standardizes the "document model" of what constitutes a web page and how it is specified.
- **CSS 3** is a styling language that enables fine-grained styling of individual elements on a page. CSS 3 defines in a consistent, standard way the details of things such as color, size, layout, and animation of page elements.
- **WebGL** provides browser support for the 3D-accelerated graphics capabilities of modern machines.
- **ECMAScript 6** is an updated version of the Javascript scripting language that has been part of the web platform since the early 1990's. More recent versions of Javascript eliminate the more problematic aspects of Javascript and make it easier for developers to create bug-free, efficient code.
- **Web Workers** are a recent addition to the web platform that allow background thread processing for long-running tasks. Before Web Workers, there was no way to run truly multi-threaded code inside a browser.

A complication in web development is that the major web browser vendors implement these technologies on their own timelines, some much more rapidly than others. Further complicating things is the reality that end users do not always upgrade their browsers frequently (or at all). This creates a landscape where there is a technology adoption curve with a very long tail. Developers of every web site need to make a conscious decision about where to draw the line choosing necessary technologies for their site to operate correctly, knowing that some users with older browsers will either have a sub-optimal experience or no access to the site at all.

For this research, we are deliberately exploring the latest standard web technologies, with the expectation that access to these technologies will become more and more common in the future. Thus, we are targeting the most recent versions of modern web browsers as of 2019, including Google Chrome, Mozilla Firefox, and Apple Safari. All three of those browsers fully support the above-listed technologies, and importantly, all three auto-update automatically,ensuring that most users of those browsers have access to the latest standard technologies.

## Requirement 2: Open source

The entire project, including all front-end (browser) and back-end (server) must be fully open-source.

No proprietary or closed licensing schemes were considered, because excellent proprietary visualization packages for MATSim already exist. Creating a competing product would be duplicative and unnecessary, and would not further the research goal of determining whether web-based technology is now advanced enough to work with MATSim outputs. The goal of this research is not to replace existing, closed, proprietary solutions, but rather to complement them.

The software developed as part of this research is licensed entirely with the GNU General Public License v3, commonly known as the "GPL" [x]. This matches the license of MATSim itself. Several other open-source licenses were considered, including the MIT License and the Apache Public License, but the benefit of sharing a common license with MATSim outweighs any perceived benefits of switching to other open licenses.

## Requirement 3: Good defaults, minimal configuration, and opinionated

Since its inception, the web platform has had a relentless focus on simplicity and smooth user onboarding. Users are accustomed to being immediately familiar with a site -- within seconds of their first interaction [x]. Because of this expectation, it is critical that this research follow current best practices for user interface (UI) and user experience (UX). Specifically, that means using familiar UI paradigms such as navigation bars and modal dialogs, separating configuration from usage, limiting settings and options to the bare minimum, and being opinionated about the way to accomplish a task.

This approach is dissimilar to some data exploration tools (e.g., QGis and Via) where extreme configurability is emphasized. Rather than providing endless options for things such as scales and color ramps, our research focuses on choosing good defaults and determining whether that is sufficient for the software to be useful.

## Requirement 4: An extensible platform

Every data visualization use case is different; there is no way to anticipate how the tool will be used. If the platform is too generic, it will be not at all useful. Conversely if only hard-coded visualizations are created for specific projects, it will be relegated to "demo-ware", meaning it is a successful technology demonstration but not actually useful for real users.

To fulfill this requirement the software platform will need to be extensible: basic capabilities and templates will be provided, but a user with some level of coding skill should be able to create new visualizations that are not anticipated by the researchers.

# Initial experiments

Based on the requirements laid out above, some initial experiments were carried out to assess various approaches before committing to a technology stack.

The Javascript code library ecosystem is extremely large. Thousands of libraries and packages available on a centralized repository, often multiple

## Visualizing time-dependent data on a geographic map

Two popular web-based Javascript libraries were tested for displaying geographic data; Leaflet [x] and Mapbox GL [2].

Leaflet

# Architecture

## Architecture: back-end

## Architecture: front-end

# Results

# Conclusions

# 9. References

[1] MATSim main reference
[2]
