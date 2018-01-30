# Guidebook Formatting Basics
## Goal
Explain the purpose and objective of each section in this area.
Break labs into groups of related activities and steps.

Examples: 
* Create Tables
* Create Access Request Fields
* Create Entitlement Fields

Use Heading 1/H1 _only_ for section titles.  All content under H1 will render as a single page when digital guidebooks are published.

## Sections
The Heading 2/H2 marker will be used to generate the navigation/table of contents within each section.

# Markdown Tips & Tricks
## General Formatting Guide
We're using GitHub not just to store/version guidebooks, but also to render to HTML.  See [Mastering Markdown](https://guides.github.com/features/mastering-markdown/) for an introduction to standard formatting.

Beyond standard Markdown, we have a few conventions you need to follow for your guidebook to render properly

## H1 & H2 relationship
Always follow your H1 lab title immediately with an H2 section title.  This is a convention we're using to automatically generate the table of contents and navigation.

## Lists
While Markdown supports nesting ordered and un-ordered lists, please avoid using nested lists in your guide book.  This is to avoid conflicts with how we style (or rather, don't) nested lists on the Developer Portal.

1. Use numbered lists for task steps
1. You don't have to manually number each step

    But sometimes you need paragraphs between steps.  In those cases, indent your paragraphs with a tab.

    Multiple paragraphs are OK too.

1. And markdown will pick up numbering where you left off.

# Images
## General

This is the general form of an image tag in Markdown with alt text in [] and the URL to the image.  The URL can be absolute or relative, but we recommend using relative images for the guidebook (as they may be re-used for other events over the course of the year).

![Absolute](https://www.servicenow.com/etc/designs/servicenow/static/img/anml/logo-rev.png)

![Relative](logo-rev.png)

## Using Paste Image in Visual Studio Code

Paste Image is a helpful extension for those of you using VSCode as your editor.  If you are a ServiceNow employee and you installed VSCode from Self Service, the extension will already be installed.  Documentation for installation & usage can be found [here](https://marketplace.visualstudio.com/items?itemName=mushan.vscode-paste-image)

# Help!

## Office Hours
Jason & Dave will be holding office hours to answer any questions you may have about Markdown, VSCode or other technical issues you may encounter while authoring your guidebooks.

Dave: Fridays at 12 PM EST / 9 AM PST - https://servicenow-cmr.webex.com/meet/Dave.Slusher

