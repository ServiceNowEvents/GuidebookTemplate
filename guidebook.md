---
description: Blast from the past
---

# Challenge: Hand-coded Markdown

## Legacy Guidebook Template

This is our guidebook template from years past when you had to write your guidebook in raw Markdown.  This only exists because we're still migrating the useful content into the exercise sections above. You can ignore this unless you want to challenge yourself to learn Markdown (see what we did there? :smile:)

### Goal

This document provides you with technical information and best practices to produce a Knowledge or CreatorCon lab guidebook consistent with current standards. The standards documented here must be applied to all guidebooks created or updated from the time you receive this template. In other words, you are not required to apply these to previous guidebooks unless that content is being updated for an upcoming event.

Click image below to watch the overview video: [![Overview video thumbnail](https://github.com/ServiceNowEvents/GuidebookTemplate/raw/master/images/Overview.png)](https://youtu.be/rXX958QvDgw)

ServiceNow uses GitHub to store/version guidebooks and render them in HTML. For instructions on setting up VS Code and git to author your guidebook, see our [Setup Guide](https://github.com/ServiceNowEvents/Guidebook-Tools-Setup-Guide/blob/master/guidebook.md). If you are unfamiliar with the basics of Markdown, see [Mastering Markdown](https://guides.github.com/features/mastering-markdown/) for an introduction to standard formatting.

Beyond standard Markdown, we have a few conventions you need to follow for your guidebook to render properly. This document covers the following topics: file directory structure, headings/sections, lists, images, writing style, and grammar & clarity.

Example of finished lab guide on developer.servicenow.com:

![Demo lab guide](images/2019-11-25-09-29-40.png)

Click the image below to understand the build process: [![Build process video thumbnail](https://github.com/ServiceNowEvents/GuidebookTemplate/raw/master/images/Build-Process.png)](https://youtu.be/uTLiXfMsuvk)

Click image below to get the details and best practices to make your lab guide zing: [![Content deep dive video thumbnail](https://github.com/ServiceNowEvents/GuidebookTemplate/raw/master/images/Content-Deep-Dive.png)](https://youtu.be/2s\_e0zvGoM4)

## File Directory Structure

### Creating your local repository

1. On your local machine, create a GitHub folder in an appropriate place (e.g. Users> Your Home> Documents).
2.  Locate the **Clone or download** (green) dropdown in the GitHub repository created for you and copy the URL.

    ![GitHub clone](https://github.com/ServiceNowEvents/GuidebookTemplate/raw/master/images/2019-10-10-09-56-55.png)
3. Open a command or terminal window on your local machine.
4.  Change directories to your GitHub folder you created above (see Mac terminal and Windows DOS examples).

    **Windows**

    ```
    C:\Users\chuck.tomasi> cd Documents\GitHub
    C:\Users\chuck.tomasi\Documents\GitHub>
    ```

    **Mac**

    ```
    /users/chuck.tomasi $ cd Documents/GitHub
    /users/chuck.tomasi/Documents/GitHub $
    ```
5.  Clone the repistory with a command similar to this:

    ```
    git clone (pasted URL)
    ```
6. You can now edit the files locally and push them to GitHub as needed.

### Files and folders

1. Your workshop/lab guide must be named **guidebook.md**.
2.  Place images in a folder named **images** (all lower case) and reference them with a relative pathname in your Markdown reference.

    ```
     ![alt-text](https://github.com/ServiceNowEvents/GuidebookTemplate/raw/master/images/2019-10-10-11-47.png)
    ```

    > Note that this document makes use of absolute URLs to the images because they do not get copied with the template. As a general practice, use relative URLs in your guidebook (see images below).
3.  Create an optional **files** folder for any files students need to download for the course, such as images, JavaScript, or csv files to import. The _files_ directory name is lowercase.

    ```
     Download the [Sample data](files/sample_data.xlsx)
    ```

    > Note that file names with spaces will break the publishing process. Replace spaces with underscores for file and image links.
4. Create an **other** folder for any additional files such as PowerPoints used to create complex diagrams, or presenter notes. These are not generally linked from the lab guide nor available to the students.

![Sample files and folders](https://github.com/ServiceNowEvents/GuidebookTemplate/raw/master/images/2019-10-10-10-24-28.png)

## Headings/Sections

### Available headings

You can use the following headings in your guidebook.

| Markdown tag | Heading level |
| ------------ | ------------- |
| #            | Heading 1     |
| ##           | Heading 2     |
| ###          | Heading 3     |

> **No other headings are allowed.**

### H1 & H2 relationship

Always follow your H1 lab title immediately with an H2 section title. This is a convention allows the import process automatically generate the table of contents and navigation (see the example figure at the top).

Use Heading 1/H1 _only_ for section titles. All content under H1 will render as a single page when digital guidebooks are published.

Example (partial):

```
# Introduction

## Goal

Convert an existing expense report process from spreadsheets to a bespoke application in ServiceNow. You'll leave this lab all without writing a single piece of code!
```

renders this index:

![Sample live index headings](https://github.com/ServiceNowEvents/GuidebookTemplate/raw/master/images/2019-11-26-14-00-30.png)

and each heading 1 renders a section this:

![Sample document headings](https://github.com/ServiceNowEvents/GuidebookTemplate/raw/master/images/2019-11-26-14-01-46.png)

### Sections

Within each Heading 1/H1 section of your lab guide, use H2 to separate the different topics or exercises.

```
## Create User Accounts

In this section you will create users for the upcoming exercises.

1. Navigate to **User Administration > Users**.

1. Click **New** at the top of the list.
```

### Allowing Attendees to Catch Up

If your lab/workshop has exercises that depend upon each other, use ServiceNow's source control integration in Studio to allow the attendee to catch up rather than hitting a dead-end.

1.  As you build your lab exercises (and guidebook), create a branch in source control as you complete each exercise. For example, create a branch "Exercise 1", with the completed first exercise. When an attendee switches to that branch, they can begin the second exercise with the first one completely done.

    > **Important!** Don't forget demo data!
2. Include the GitHub Companion update set in your CloudLabs ICE Package.
3. Provide instructions at the end of each exercise to allow any attendees who did not successfully complete the lab the ability to use GitHub companion to switch branches and continue learning.

## Lists

* While Markdown supports nesting ordered and un-ordered lists, please avoid using nested lists in your guide book. This is to avoid conflicts with how we style (or rather, do not) nested lists on the Developer Portal.
  1. Use numbered lists for task steps. All of these steps start with _1._
  2.  You do not have to manually number each step.

      But sometimes you need paragraphs between steps. In those cases, indent your paragraphs with a tab.

      Multiple paragraphs are OK too.
  3. And markdown will pick up numbering where you left off.
  4. Place a blank line between ordered and unordered lists for clarity.
* Indent supporting images and text to allow numbered lists to continue

## Images

### General Image Information

This is the general form of an image tag in Markdown with alt text in \[] and the URL to the image. The URL can be absolute or relative. We recommend using relative images for the guidebook (as they may be re-used for other events over the course of the year).

```
![Absolute](https://www.servicenow.com/content/dam/servicenow-assets/images/meganav/servicenow-header-logo.svg)

![Relative](images/2018-now-logo.png)
```

* Inline images must be smaller than 100 pixels wide.
* All images MUST have alternate text defined for accessibility compliance. This is the part of the image markdown in the square brackets. This text should describe the image in a way that allows a screen reader to provide context to someone who cannot see the image.
*   DO NOT use a screenshot as a replacement for text as this is not usable for people with accessibility requirements.

    For example, do not say “configure the record as shown \<insert screenshot>”. You can have a screenshot showing the configured record but you must also have text outside of the screenshot to explain what to do.
*   Screenshot images should have a border applied in : 1 pt, dark gray (hex #424242, dec 66,66,66) (This should be .75 px, but Snagit only supports integers and points, not pixels).

    ![Adding a border](https://github.com/ServiceNowEvents/GuidebookTemplate/raw/master/images/2019-10-10-10-46-35.png)
*   Avoid entire screenshots when not needed

    Keep in mind that many guidebook users may be viewing your content using mobile devices. Full screenshots are difficult to read on a tablet or mobile phone. For example, this image of Studio is difficult to read on a desktop, let alone a small screen.

    **Bad**:

    ![Poor screenshot example](https://github.com/ServiceNowEvents/GuidebookTemplate/raw/master/images/2019-10-11-08-40-50.png)

    Providing instructions to click _Create Application File_ are not much help. Instead, take a screenshot of the area of focus _in context_ (with some additional elements in the shot or partially in the shot) to help the viewer locate where you want them to focus.

    **Good**:

    ![Good screenshot example](https://github.com/ServiceNowEvents/GuidebookTemplate/raw/master/images/2019-10-11-08-43-59.png)
*   If you find you need a full screen shot...

    There will be times when you need an entire screenshot in your lab guide. Use these sparingly - often to show a "finished product" such as a dashboard layout.

    *   Make the font as large as possible

        Use your browser's zoom feature to make the font as large as possible without affecting the layout of the screen. This improves the readability.
    *   Use arrows to indicate areas of focus

        If you need to draw attention to a screen element in a larger context, use an arrow and label to clearly indicate where the reader should focus.

        ![Simple annotation](https://github.com/ServiceNowEvents/GuidebookTemplate/raw/master/images/2019-10-11-08-53-17.png)
* Do not exceed image width of 1024px
*   When you have an image representing multiple steps, provide numeric indicators and reference them in the text

    Example:

    1. In the left column, click **Data Model** (1), then in the middle, click **Table** (2), and finally click **Create** in the lower right (3).

    ![Multiple step annotation](https://github.com/ServiceNowEvents/GuidebookTemplate/raw/master/images/2019-10-11-08-57-24.png)

## Writing Style

### General

* Escape special characters in Markdown. This includes ()\[]{}<>.
*   Identify questions and notes with the Markdown prefix **>**

    > Note: If you get a 403 error, check your headers.

    > Question: Did the list show 5 records?
*   As the learner reads your guidebook, provide them fewer details.

    For example, after you have given the six-step instructions to create a user record, you do not provide the same six steps for each additional user record. Simply give instructions such as: _Repeat steps 1-6 to create two additional user accounts for Tom Harrington, and Dory Williams._ Assume the learner is learning! This also makes it easier to maintain the guidebook should any of the details change.
*   Use tables when providing repetitive data entry instructions

    Example:

    1.  Fill in the New account form with the data from this table:

        | Field        | Value                       |
        | ------------ | --------------------------- |
        | Name         | Acme Corp                   |
        | Location     | 333 Cliffside Rd, Tucson AZ |
        | Contact name | Wile E. Coyote              |
*   Add a reference section to the docs pages or other helpful material at the end of each lab exercise.

    **Reference**:

    * [Flow Designer](https://docs.servicenow.com/bundle/newyork-servicenow-platform/page/administer/flow-designer/concept/flow-designer.html)
    * [Community](https://community.servicenow.com)
*   Validate all code against [technical best practices](https://developer.servicenow.com/app.do#!/catlist/technical\_best\_practices?v=newyork).

    Examples include:

    *   Avoid dot walking to a sys\_id. A reference field value _is_ a sys\_id, so dot-walking is redundant and costs an extra database query.

        **NO**:

        ```javascript
        var id = current.caller_id.sys_id;
        ```

        **YES**:

        ```javascript
        var id = current.getValue('caller_id');
        ```
    *   Use GlideRecord getValue() instead of using dotted-notation. Using dotted-notation can return incorrect values as the dotted field is an object (making work in Service Portal frustrating) and GlideRecord is a pointer (making values in loops troublesome). getValue() also allows you to use variables for field names.

        **NO**:

        ```javascript
        var location = userGr.location;
        ```

        **YES**:

        ```javascript
        var location = userGr.getValue('location');
        ```
    *   When you need to dot-walk to a reference value, use toString(). Do not use toString() in place of getValue() in the previous example.

        **NO**:

        ```javascript
        var locationID = current.caller_id.location;
        ```

        **YES**:

        ```javascript
        var locationID = current.caller_id.location.toString();
        ```
    *   Use setValue() instead of dotted notation when setting a field value.

        **NO**:

        ```javascript
        incGr.state = 5;
        ```

        **YES**:

        ```javascript
        incGr.setValue('state', 5);
        ```
    *   Avoid hard coding sys\_ids. Use a property value, or use the setDisplayValue() method (or both) where you can. sys\_ids and other hard coded strings are difficult to read and maintain.

        **NO**:

        ```javascript
        current.assignment_group = '3176fe10db4e1340cbf6d5b0cf9619cd';
        ```

        **YES**: Set a system property like:

        | Field | Value                             |
        | ----- | --------------------------------- |
        | Name  | my\_app.default.assignment\_group |
        | Value | Help Desk                         |

        ```javascript
        current.assignment_group.setDisplayValue(gs.getProperty('my_app.default.assignment_group'));
        ```
    *   Use GlideRecord setLimit(1) when you only need one record to check if a record exists. This can greatly speed up queuries.

        **NO**:

        ```javascript
        var incGr = new GlideRecord('incident');
        incGr.addQuery('active', true);
        incGr.addQuery('priority', 1);
        incGr.query();

        if (incGr.next()) {
            return incGr;
        }
        ```

        **YES**:

        ```javascript
         var incGr = new GlideRecord('incident');
        incGr.addQuery('active', true);
        incGr.addQuery('priority', 1);
        incGr.setLimit(1);
        incGr.query();

        if (incGr.next()) {
            return incGr;
        }
        ```

### Emphasis

* Do not use "quotes" for emphasis.
* Use **bold** for:
  * Anything users click, type, or drag
    * Example: Click the **Save** button.
  * Application Navigator paths
    * Example: Use the Application Navigator to open **System Applications > Studio**.
  * Application Explore paths
  * Example: To open an applet in Studio, use the Application Explorer to open **Mobile Studio > Applets > \<applet name>**.
* Use _italics_ for:
  * Application names
    * Open the _NeedIt_ application in Studio.
  * Application file names
    * Example: Configure the _Update Record_ action.
    * Example: The _NeedIt When needed field date_ Business Rule prevents creating _NeedIt_ records with _When needed_ field values in the past.
  * Field names and values
    * Example: _Name_: **Shopping List**
    * Example: In the example, the _Starting Number_ field contains a 4-digit number.
    * Example: When the _Active_ field is _true_...
  * Related list names
    * Example: Click the **New** button on the _HTTP Methods_ related list.
  * Dialog names
    * In the _Select Application_ dialog, click the **NeedIt** link to open the _NeedIt_ application for editing.
* Use < > around variable data or data a user selects. (Do not forget to use backslash before < and >.)
  * Example: To open an applet in Studio, use the Application Explorer to open **Mobile Studio > Applets > \<applet name>**.
  * Example: _When needed_: **\<select any date in the future>**
* Use ( ) for values that are automatically populated.
  * Example: _Scope_: **(This value is automatically populated)**
* Use (path > item) for data pills.
  * Example: _Record_: **(Trigger > NeedIt Record)**
* Use \[ ] to separate components of multi-part fields and conditions.
  * Example: _Fields_: **\[State] \[Approved]**
  * Example: _Condition_: **\[Short description] \[contains]\[printer]**

### Numbering

Numbering renders in the proper sequence regardless of the numbers used in the markdown and restarts at H2s and parent list items. To keep things simple, begin each numbered line with a _1._ to ensure proper numbering.

For example, when adding application files to Studio, always use the same verbiage:

1. Create a UI Policy.
   1. In Studio, click the **Create Application File** button.
   2. In the _Filter..._ field enter the text **UI Policy** OR select **Client Development** from the categories in the left hand pane.
   3. Select **UI Policy** in the middle pane as the file type then click the **Create** button.
2.  Configure the UI Policy:

    | Field             | Value                                                   |
    | ----------------- | ------------------------------------------------------- |
    | Table             | **NeedIt \[x\_\<your\_company\_code>\_needit\_needit]** |
    | Active            | **Selected (checked)**                                  |
    | Short description | **NeedIt show or hide Other field**                     |

### Code

*   Surround code in triple-backtick marks (\`\`\`)

    Surrounding your code in \`\`\` marks formats the code to be easily copied and pasted. Using the language inside the starting ticks makes enables keyword highlighting as well.

    ```javascript
    var incGr = new GlideRecord('incident');
    incGr.query();
    var count = incGr.getRowCount();
    ```
*   If your script exceeds more than 20 lines, create it as a text file in the _files/_ folder of your repo. A .zip of files will be distributed with your guidebook. For example:

    Copy the contents of the **rest\_response\_processing.js.txt** into the Script step created in the previous step.

## Grammar and Clarity

* For mobile instructions, use "tap" instead of "click"
  * **NO**: Click the camera icon.
  * **YES**: Tap the camera icon.
* Use "Click" or "Tap", not "Click on" or "Tap on"
  * **NO**: At the bottom of the form, click on the **Submit** button.
  * **YES**: At the bottom of the form, Click the **Submit** button.
* Avoid passive sentences. If you find yourself using words like _should_ and _will_, rewrite your instructions to be more active.
  * **NO**: The form will display the number of records.
  * **YES**: The form displays the number of records.
  * **NO**: You should see a screen a list with five rows.
  * **YES**: A list with five rows is displayed.
* Avoid using _you_ and other second-person pronouns in concept pages.
* NEVER use _we_, _our_, and other first-person pronouns.
* Do not use "once" to indicate continuation.
  * **NO**: Once you complete the form, click **Save**.
  * **YES**: When you have completed the form, click **Save**.
* Do NOT use contractions.
* Use the Oxford comma for this, that, and the other things.
* Log in is a verb and login is an adjective or noun. “Use the login screen to log in to your instance.” (Notice it is not log into because the verb is ‘log in’) Same with sign in / signin and log out / logout.
* UTILIZE should NEVER be used in our content as it means to use something not fit for purpose. As in, “make do with”.
* Give clarity as to where someone should look for something.
  * **NO**: Click **Save**.
  * **YES**: In the Properties dialog, click the **Save** button.
* Do not use positional words unless required.
  * **NO**: In the screenshot below...
  * **YES**: In the example...

## Helpful resources

* [Podcast: Break Point - Effective Presentations with Julian Mills - Part 1 - Preperation](https://omny.fm/shows/break-point/effective-presentations-with-julian-mills-part-1-p)
* [Podcast: Break Point - Effective Presentations with Julian Mills - Part 2 - Common mistakes](https://omny.fm/shows/break-point/break-point-034)
