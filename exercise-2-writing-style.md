# Exercise 2: Writing Style

## Goal

Learn best style practices for writing a guidebook.

## General

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

## Emphasis

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

## Numbering

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

## Code

*   Use code blocks to make the code to be easily copied and pasted. Selecting the syntax highlight rule on the code block makes the snippet more readable.

    ```javascript
    var incGr = new GlideRecord('incident');
    incGr.query();
    var count = incGr.getRowCount();
    ```
*   If your script exceeds more than 20 lines, attach is as a text file. For example:

    Copy the contents of the **rest\_response\_processing.js.txt** into the Script step created in the previous step.

## Grammas and carity

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

##
