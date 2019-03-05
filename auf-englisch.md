---
title: A web-based data visualization platform for MATSim
author: \textbf{William Charlton}, Technische Universität Berlin, Germany
---

---

## Introduction

MATSim (Horni, et. al, 2016) is widely used for transportation research in academic settings, and is gaining momentum as a tool ready for real-world planning contexts. As MATSim moves from the confines of academic research to a more public-facing role, a notable gap is apparent: there are no web-based, interactive tools available for disseminating MATSim results. This creates a challenge for using MATSim in public policy settings: only people who have extensive technical knowledge and access to specialized software can meaningfully examine and explore the results.

This research attempts to fill this gap by building an open web-based visualization platform which is specifically designed to complement MATSim.

## Requirements

The research team at TU Berlin convened several "blank slate" discussions before any code was written. The following requirements emerged from those discussions.

- **Requirement 1: Modern web-browser based.** Several recent web technologies make this research possible: HTML 5, CSS 3, WebGL, ECMA Script 6, and Web Workers. Unfortunately, end users do not always upgrade their browsers frequently. This creates a technology adoption curve with a very long "tail". We have chosen the latest web technologies, with the expectation that they will become more common in the future.
- **Requirement 2: Open source.** The entire project is fully open-source, licensed under the GNU General Public License v3.
- **Requirement 3: Use good defaults, with minimal configuration.** Web users are accustomed to being immediately familiar with a site -- often within seconds of their first interaction. It is critical that this research follow current best practices for user interface and user experience.
- **Requirement 4: An extensible platform.** Every data visualization use case is different. Basic capabilities and templates will be provided, but a user with some level of coding skill should be able to create new visualizations that are not anticipated by the researchers.

## Initial experiments

Initial experiments were carried out to assess various approaches before committing to a front-end technology stack. Note that the back-end is described in a companion paper by J. Laudan.

**Visualizing data on a geographic map.** Two popular web-based Javascript libraries were tested for displaying geographic data; Leaflet and Mapbox GL. Mapbox GL handled large datasets much better than Leaflet. Mapbox GL's use of 3D vector graphic mapping instead of preset tiles made for a much smoother visual experience.

**Non-geographic data.** Experimentation with many various graphing and charting libraries led to the package Vega-Lite (Satyanarayan, 2016). Notably, Vega-lite follows a "grammar of graphics" declarative syntax, as popularized by Wilkinson (2005).

## Results: the current state of the tool

A working instance of the platform is now online and available at https://viz.vsp.tu-berlin.de. Sample datasets are uploaded, and pre-built visualizations are publicly accessible, as a demonstration of the platform's current state.

Several types of aggregate visualizations are currently operational:

- Origin/destination flows between aggregate areas
- Link flows by time of day
- A transit supply explorer
- Sankey diagrams, which depict flows between between multiple choices, such as shifts in mode between two scenarios
- Emissions levels on a geographic grid basis

And one disaggregate visualization is available:

- A vehicle flow simulation, with vehicles traveling in real-time on the network.

**Visualization plug-ins.** New visualizations can be produced rapidly and added to the framework to generate new capabilities. The Vue "single page application" component architecture enables this. To create a new visualization, the developer copies an existing blank visualization template, specifies the inputs and parameters required, and then modifies the javascript code to meet their needs. This currently requires broad coding skill in Javascript; it is not a system that is "point-and-click" like an online data exploration tool.

See the following screenshots in _Figure 1_ for examples of the current state of the user interface.

![Sample visualizations, 1a - 1f](all-figures.png)

## Performance

Even with modern hardware and the latest browsers, it is challenging to produce performant, visually pleasing results with disaggregate MATSim data. For example, the vehicle flow simulation depends heavily on the back-end server to produce simulation "frames" for the browser.

Aggregate data is much easier to visualize. Further work needs to be done to leverage the back-end server capabilities we now have available.

## Conclusions and outlook

Experimenting with the various technologies and getting everything working together was an enormous task, but the platform is now quite stable.

A new visualization can be generated by the researchers in a matter of days. It has been encouraging to see visualizations go from ideation to rough draft in such a short time.

In the meanwhile, the world of data visualization has not stood still. Major data visualization efforts from well-funded companies such as Uber have been recently released. There are legitimate questions about how this work could be superceded by large, professional coding teams.

Despite these concerns, the MATSim visualization framework is operational and is beginning to be useful for researchers. This bodes well for its further development.

All code is available on the MATSim Github site, at https://github.com/matsim-org/viz.
