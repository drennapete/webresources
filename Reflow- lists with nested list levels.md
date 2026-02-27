<!-- al:1 -->

## Example lists with nested lists

<!-- al:2 -->

The following two examples are meant to demonstrate why Success Criterion 1.4.10 Reflow allows for a whole list to scroll in two-dimensions while ensuring individual list items still fit within the 320 CSS pixel width.

<!-- al:3 -->

Zooming in to 400% on an original browser viewport width of 1280 pixels, the difference between a list which allows two-dimensional scrolling vs one that limits the entire list and its nested lists to a 320px width can be seen.

<!-- al:4 -->

-   In the first example, although the list is horizontally scrollable, you can scroll to the start of a nested list, identifiable via the indentation and by the starting bullet of a list item. Reading the content of that nest listitem and its sibling list items requires one only scroll in a single direction (vertically). To read the content of a parent or child list, one again can horiztonally scroll to the start of that item, and then only scroll in a single direction to read.
-   In the second example, while the list does not require horizontal scrolling and technically meets the requirement, readability declines from the 3rd level of nesting onward. By the 4th level, each letter breaks onto a new line, making the content unnecessarily difficult to read.

<!-- al:5 -->

Note that there are additional styling updates that one might make, or futher manipulations to the lists to present the content in a differnet manner, bypassing the need for any horizontal scrolling. And those would be ways to adjust content to meet Reflow. But this example is also a valid means to meet the Reflow SC.

<!-- al:6 -->

### Example 1

<!-- al:7 -->

-   <!-- al:8 -->

    Make a list using one of the HTML list elements, or even an ARIA `role=list` container.

    <!-- al:9 -->

    -   <!-- al:10 -->

        There are three types of lists in HTML which can contain list items `li` elements.

        <!-- al:11 -->

        -   <!-- al:12 -->

            the `ul` element

        -   <!-- al:13 -->

            the `ol` element

        -   <!-- al:14 -->

            the `menu` element

    -   <!-- al:15 -->

        Another type of list, description lists, exist as well - but they do not contain list items (`li` elements).

-   <!-- al:16 -->

    Neither the start or end tags of any of the HTML list elements are omissible.

    <!-- al:17 -->

    -   <!-- al:18 -->

        The end tags of `li` elements can be omitted if the `li` element is immeditely followed by another `li` element or there is no more content in the parent list element.

    -   <!-- al:19 -->

        The list marker for each `li` element is initially based on the parent list element used.

        <!-- al:20 -->

        -   <!-- al:21 -->

            The list maker can be modified by using CSS,

            <!-- al:22 -->

            -   <!-- al:23 -->

                A list item's `::marker` can be styled similarly to other pseudo elements, like `::before` and `::after`. Use it to modify or restyle or create custom unordered list markers.

            -   <!-- al:24 -->

                Using the `::before` pseudo element, one can use the CSS `counter` and `content` properties to create custom incrementing numeration for list items.

        -   <!-- al:25 -->

            or the list marker can be modifed by using the `type` attribute, if the parent list element is an `ol` element. The `type` attribute is obsolete on the `ul` element, and is not allowed on the `menu` element.

-   <!-- al:26 -->

    Validate your markup to make sure your lists are properly structured.


<!-- al:27 -->

### Example 2

<!-- al:28 -->

-   <!-- al:29 -->

    Make a list using one of the HTML list elements, or even an ARIA `role=list` container.

    <!-- al:30 -->

    -   <!-- al:31 -->

        There are three types of lists in HTML which can contain list items `li` elements.

        <!-- al:32 -->

        -   <!-- al:33 -->

            the `ul` element

        -   <!-- al:34 -->

            the `ol` element

        -   <!-- al:35 -->

            the `menu` element

    -   <!-- al:36 -->

        Another type of list, description lists, exist as well - but they do not contain list items (`li` elements).

-   <!-- al:37 -->

    Neither the start or end tags of any of the HTML list elements are omissible.

    <!-- al:38 -->

    -   <!-- al:39 -->

        The end tags of `li` elements can be omitted if the `li` element is immeditely followed by another `li` element or there is no more content in the parent list element.

    -   <!-- al:40 -->

        The list marker for each `li` element is initially based on the parent list element used.

        <!-- al:41 -->

        -   <!-- al:42 -->

            The list maker can be modified by using CSS,

            <!-- al:43 -->

            -   <!-- al:44 -->

                A list item's `::marker` can be styled similarly to other pseudo elements, like `::before` and `::after`. Use it to modify or restyle or create custom unordered list markers.

            -   <!-- al:45 -->

                Using the `::before` pseudo element, one can use the CSS `counter` and `content` properties to create custom incrementing numeration for list items.

        -   <!-- al:46 -->

            or the list marker can be modifed by using the `type` attribute, if the parent list element is an `ol` element. The `type` attribute is obsolete on the `ul` element, and is not allowed on the `menu` element.

-   <!-- al:47 -->

    Validate your markup to make sure your lists are properly structured.