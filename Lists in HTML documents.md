[previous](text.html)   [next](tables.html)   [contents](../cover.html#minitoc)   [elements](../index/elements.html)   [attributes](../index/attributes.html)   [index](../index/list.html)

* * *

<!-- al:1 -->

# 10 Lists

<!-- al:2 -->

**Contents**

<!-- al:3 -->

1.  [Introduction to lists](#h-10.1)
2.  [Unordered lists (UL), ordered lists (OL), and list items (LI)](#h-10.2)
3.  [Definition lists: the DL, DT, and DD elements](#h-10.3)

    <!-- al:4 -->

    1.  [Visual rendering of lists](#h-10.3.1)
4.  [The DIR and MENU elements](#h-10.4)

<!-- al:5 -->

## 10.1 Introduction to lists

HTML offers authors several mechanisms for specifying lists of information. All lists must contain one or more list elements. Lists may contain:

<!-- al:6 -->

-   Unordered information.
-   Ordered information.
-   Definitions.

<!-- al:7 -->

The previous list, for example, is an unordered list, created with the [UL](lists.html#edef-UL) element:

<!-- al:8 -->

<UL>
<LI>Unordered information.
<LI>Ordered information.
<LI>Definitions.
</UL>

<!-- al:9 -->

An ordered list, created using the [OL](lists.html#edef-OL) element, should contain information where order should be emphasized, as in a recipe:

<!-- al:10 -->

1.  Mix dry ingredients thoroughly.
2.  Pour in wet ingredients.
3.  Mix for 10 minutes.
4.  Bake for one hour at 300 degrees.

<!-- al:11 -->

Definition lists, created using the [DL](lists.html#edef-DL) element, generally consist of a series of term/definition pairs (although definition lists may have other applications). Thus, when advertising a product, one might use a definition list:

<!-- al:12 -->

**Lower cost**

<!-- al:13 -->

The new version of this product costs significantly less than the previous one!

<!-- al:14 -->

**Easier to use**

<!-- al:15 -->

We've changed the product so that it's much easier to use!

<!-- al:16 -->

**Safe for kids**

<!-- al:17 -->

You can leave your kids alone in a room with this product and they won't get hurt (not a guarantee).

<!-- al:18 -->

defined in HTML as:

<!-- al:19 -->

<DL>
<DT><STRONG>Lower cost</STRONG>
<DD>The new version of this product costs significantly less than the
previous one!
<DT><STRONG>Easier to use</STRONG>
<DD>We've changed the product so that it's much easier to use!
<DT><STRONG>Safe for kids</STRONG>
<DD>You can leave your kids alone in a room with this product and
they won't get hurt (not a guarantee).
</DL>

<!-- al:20 -->

Lists may also be nested and different list types may be used together, as in the following example, which is a definition list that contains an unordered list (the ingredients) and an ordered list (the procedure):

<!-- al:21 -->

**The ingredients:**

<!-- al:22 -->

<!-- al:23 -->

-   100 g. flour
-   10 g. sugar
-   1 cup water
-   2 eggs
-   salt, pepper

<!-- al:24 -->

**The procedure:**

<!-- al:25 -->

<!-- al:26 -->

1.  Mix dry ingredients thoroughly.
2.  Pour in wet ingredients.
3.  Mix for 10 minutes.
4.  Bake for one hour at 300 degrees.

<!-- al:27 -->

**Notes:**

<!-- al:28 -->

The recipe may be improved by adding raisins.

<!-- al:29 -->

The exact presentation of the three list types depends on the user agent. We discourage authors from using lists purely as a means of indenting text. This is a stylistic issue and is properly handled by style sheets.

<!-- al:30 -->

## 10.2 Unordered lists (UL), ordered lists (OL), and list items ([LI](lists.html#edef-LI))

<!-- al:31 -->

<!ELEMENT [UL](lists.html#edef-UL) - - (LI)+                 -- unordered list -->
<!ATTLIST UL
  [%attrs;](../sgml/dtd.html#attrs)                              -- [%coreattrs](../sgml/dtd.html#coreattrs), [%i18n](../sgml/dtd.html#i18n), [%events](../sgml/dtd.html#events) --
  >
<!ELEMENT [OL](lists.html#edef-OL) - - (LI)+                 -- ordered list -->
<!ATTLIST OL
  [%attrs;](../sgml/dtd.html#attrs)                              -- [%coreattrs](../sgml/dtd.html#coreattrs), [%i18n](../sgml/dtd.html#i18n), [%events](../sgml/dtd.html#events) --
  >

<!-- al:32 -->

*Start tag: **required**, End tag: **required***

<!-- al:33 -->

<!ELEMENT [LI](lists.html#edef-LI) - O ([%flow;](../sgml/dtd.html#flow))\*             -- list item -->
<!ATTLIST LI
  [%attrs;](../sgml/dtd.html#attrs)                              -- [%coreattrs](../sgml/dtd.html#coreattrs), [%i18n](../sgml/dtd.html#i18n), [%events](../sgml/dtd.html#events) --
  >

<!-- al:34 -->

*Start tag: **required**, End tag: **optional***

<!-- al:35 -->

*Attribute definitions*

<!-- al:36 -->

type  =  *style-information* [\[CI\]](../types.html#case-insensitive)

<!-- al:37 -->

[**Deprecated.**](../conform.html#deprecated) This attribute sets the style of a list item. Currently available values are intended for visual user agents. [Possible values](#type-values) are described below (along with case information).

<!-- al:38 -->

start = [*number*](../types.html#type-number) [\[CN\]](../types.html#case-neutral)

<!-- al:39 -->

[**Deprecated.**](../conform.html#deprecated) For [OL](lists.html#edef-OL) only. This attribute specifies the starting number of the first item in an ordered list. The default starting number is "1". Note that while the value of this attribute is an integer, the corresponding label may be non-numeric. Thus, when the list item style is uppercase latin letters (A, B, C, ...), start=3 means "C". When the style is lowercase roman numerals, start=3 means "iii", etc.

<!-- al:40 -->

value = [*number*](../types.html#type-number) [\[CN\]](../types.html#case-neutral)

<!-- al:41 -->

[**Deprecated.**](../conform.html#deprecated) For [LI](lists.html#edef-LI) only. This attribute sets the number of the current list item. Note that while the value of this attribute is an integer, the corresponding label may be non-numeric (see the [start](lists.html#adef-start) attribute).

<!-- al:42 -->

compact [\[CI\]](../types.html#case-insensitive)

<!-- al:43 -->

[**Deprecated.**](../conform.html#deprecated) When set, this boolean attribute gives a hint to visual user agents to render the list in a more compact way. The interpretation of this attribute depends on the user agent.

<!-- al:44 -->

*Attributes defined elsewhere*

<!-- al:45 -->

-   [id](global.html#adef-id), [class](global.html#adef-class) ([document-wide identifiers](../struct/global.html#id-and-class))
-   [lang](dirlang.html#adef-lang) ([language information](../struct/dirlang.html#language-info)), [dir](dirlang.html#adef-dir) ([text direction](../struct/dirlang.html#bidirection))
-   [title](global.html#adef-title) ([element title](../struct/global.html#title))
-   [style](../present/styles.html#adef-style) ([inline style information](../present/styles.html#style-element))
-   [onclick](../interact/scripts.html#adef-onclick), [ondblclick](../interact/scripts.html#adef-ondblclick), [onmousedown](../interact/scripts.html#adef-onmousedown), [onmouseup](../interact/scripts.html#adef-onmouseup), [onmouseover](../interact/scripts.html#adef-onmouseover), [onmousemove](../interact/scripts.html#adef-onmousemove), [onmouseout](../interact/scripts.html#adef-onmouseout), [onkeypress](../interact/scripts.html#adef-onkeypress), [onkeydown](../interact/scripts.html#adef-onkeydown), [onkeyup](../interact/scripts.html#adef-onkeyup) ([intrinsic events](../interact/scripts.html#events))

<!-- al:46 -->

Ordered and unordered lists are rendered in an identical manner except that visual user agents number ordered list items. User agents may present those numbers in a variety of ways. Unordered list items are not numbered.

<!-- al:47 -->

Both types of lists are made up of sequences of list items defined by the LI element (whose end tag may be omitted).

<!-- al:48 -->

This example illustrates the basic structure of a list.

<!-- al:49 -->

<UL>
   <LI> *... first list item...*
   <LI> *... second list item...*
   ...
</UL>

<!-- al:50 -->

Lists may also be nested:

<!-- al:51 -->

DEPRECATED EXAMPLE:

<!-- al:52 -->

<UL>
     <LI> *... Level one, number one...*
     <OL>
        <LI> *... Level two, number one...*
        <LI> *... Level two, number two...*
        <OL start="10">
           <LI> *... Level three, number one...*
        </OL>
        <LI> *... Level two, number three...*
     </OL>
     <LI> *... Level one, number two...*
</UL>

<!-- al:53 -->

***Details about number order.** In ordered lists, it is not possible to continue list numbering automatically from a previous list or to hide numbering of some list items. However, authors can reset the number of a list item by setting its value attribute. Numbering continues from the new value for subsequent list items. For example:*

<!-- al:54 -->

<ol>
<li value="30"> makes this list item number 30.
<li value="40"> makes this list item number 40.
<li> makes this list item number 41.
</ol>

<!-- al:55 -->

## 10.3 Definition lists: the DL, DT, and DD elements

<!-- al:56 -->

<!-- definition lists - DT for term, DD for its definition -->

<!ELEMENT [DL](lists.html#edef-DL) - - (DT|DD)+              -- definition list -->
<!ATTLIST DL
  [%attrs;](../sgml/dtd.html#attrs)                              -- [%coreattrs](../sgml/dtd.html#coreattrs), [%i18n](../sgml/dtd.html#i18n), [%events](../sgml/dtd.html#events) --
  >

<!-- al:57 -->

*Start tag: **required**, End tag: **required***

<!-- al:58 -->

<!ELEMENT [DT](lists.html#edef-DT) - O ([%inline;](../sgml/dtd.html#inline))\*           -- definition term -->
<!ELEMENT [DD](lists.html#edef-DD) - O ([%flow;](../sgml/dtd.html#flow))\*             -- definition description -->
<!ATTLIST (DT|DD)
  [%attrs;](../sgml/dtd.html#attrs)                              -- [%coreattrs](../sgml/dtd.html#coreattrs), [%i18n](../sgml/dtd.html#i18n), [%events](../sgml/dtd.html#events) --
  >

<!-- al:59 -->

*Start tag: **required**, End tag: **optional***

<!-- al:60 -->

*Attributes defined elsewhere*

<!-- al:61 -->

-   [id](global.html#adef-id), [class](global.html#adef-class) ([document-wide identifiers](../struct/global.html#id-and-class))
-   [lang](dirlang.html#adef-lang) ([language information](../struct/dirlang.html#language-info)), [dir](dirlang.html#adef-dir) ([text direction](../struct/dirlang.html#bidirection))
-   [title](global.html#adef-title) ([element title](../struct/global.html#title))
-   [style](../present/styles.html#adef-style) ([inline style information](../present/styles.html#style-element))
-   [onclick](../interact/scripts.html#adef-onclick), [ondblclick](../interact/scripts.html#adef-ondblclick), [onmousedown](../interact/scripts.html#adef-onmousedown), [onmouseup](../interact/scripts.html#adef-onmouseup), [onmouseover](../interact/scripts.html#adef-onmouseover), [onmousemove](../interact/scripts.html#adef-onmousemove), [onmouseout](../interact/scripts.html#adef-onmouseout), [onkeypress](../interact/scripts.html#adef-onkeypress), [onkeydown](../interact/scripts.html#adef-onkeydown), [onkeyup](../interact/scripts.html#adef-onkeyup) ([intrinsic events](../interact/scripts.html#events))

<!-- al:62 -->

Definition lists vary only slightly from other types of lists in that list items consist of two parts: a term and a description. The term is given by the [DT](lists.html#edef-DT) element and is restricted to inline content. The description is given with a [DD](lists.html#edef-DD) element that contains block-level content.

<!-- al:63 -->

Here is an example:

<!-- al:64 -->


<DL>
  <DT>Dweeb
  <DD>young excitable person who may mature
    into a <EM>Nerd</EM> or <EM>Geek</EM>

  <DT>Hacker
  <DD>a clever programmer

  <DT>Nerd
  <DD>technically bright but socially inept person

</DL>

<!-- al:65 -->

Here is an example with multiple terms and descriptions:

<!-- al:66 -->

<DL>
   <DT>Center
   <DT>Centre
   <DD> A point equidistant from all points
              on the surface of a sphere.
   <DD> In some field sports, the player who
              holds the middle position on the field, court,
              or forward line.
</DL>

<!-- al:67 -->

Another application of [DL](lists.html#edef-DL), for example, is for marking up dialogues, with each [DT](lists.html#edef-DT) naming a speaker, and each [DD](lists.html#edef-DD) containing his or her words.

<!-- al:68 -->

### 10.3.1 Visual rendering of lists

<!-- al:69 -->

***Note.** The following is an informative description of the behavior of some current visual user agents when formatting lists. Style sheets allow better control of list formatting (e.g., for numbering, language-dependent conventions, indenting, etc.).*

<!-- al:70 -->

Visual user agents generally indent nested lists with respect to the current level of nesting.

<!-- al:71 -->

For both [OL](lists.html#edef-OL) and [UL](lists.html#edef-UL), the [type](lists.html#adef-type-LI) attribute specifies rendering options for visual user agents.

<!-- al:72 -->

For the [UL](lists.html#edef-UL) element, possible values for the [type](lists.html#adef-type-LI) attribute are disc, square, and circle. The default value depends on the level of nesting of the current list. These values are case-insensitive.

<!-- al:73 -->

How each value is presented depends on the user agent. User agents should attempt to present a "disc" as a small filled-in circle, a "circle" as a small circle outline, and a "square" as a small square outline.

<!-- al:74 -->

A graphical user agent might render this as:

<!-- al:75 -->

![A possible rendering of a disc](../images/lidisc.gif)for the value "disc"
![A possible rendering of a circle](../images/licircle.gif)for the value "circle"
![A possible rendering of a square](../images/lisquare.gif)for the value "square"

<!-- al:76 -->

For the [OL](lists.html#edef-OL) element, possible values for the [type](lists.html#adef-type-LI) attribute are summarized in the table below (they are case-sensitive):

<!-- al:77 -->

| Type | Numbering style |
| --- | --- |
| 1 | arabic numbers | 1, 2, 3, ... |
| a | lower alpha | a, b, c, ... |
| A | upper alpha | A, B, C, ... |
| i | lower roman | i, ii, iii, ... |
| I | upper roman | I, II, III, ... |

<!-- al:78 -->

Note that the [type](lists.html#adef-type-LI) attribute is [deprecated](../conform.html#deprecated) and list styles should be handled through style sheets.

<!-- al:79 -->

For example, using CSS, one may specify that the style of numbers for list elements in a numbered list should be lowercase roman numerals. In the excerpt below, every [OL](lists.html#edef-OL) element belonging to the class "withroman" will have roman numerals in front of its list items.

<!-- al:80 -->

<STYLE type="text/css">
OL.withroman { list-style-type: lower-roman }
</STYLE>
<BODY>
<OL class="withroman">
<LI> Step one ...
<LI> Step two ...
</OL>
</BODY>

<!-- al:81 -->

The rendering of a definition list also depends on the user agent. The example:

<!-- al:82 -->

<DL>
  <DT>Dweeb
  <DD>young excitable person who may mature
    into a <EM>Nerd</EM> or <EM>Geek</EM>

  <DT>Hacker
  <DD>a clever programmer

  <DT>Nerd
  <DD>technically bright but socially inept person
</DL>

<!-- al:83 -->

might be rendered as follows:

<!-- al:84 -->

Dweeb
       young excitable person who may mature into a *Nerd* or *Geek*
Hacker
       a clever programmer
Nerd
       technically bright but socially inept person

<!-- al:85 -->

## 10.4 The DIR and MENU elements

<!-- al:86 -->

**DIR and MENU are [deprecated](../conform.html#deprecated).**

<!-- al:87 -->

See the [Transitional DTD](../sgml/loosedtd.html#dir) for the formal definition.

<!-- al:88 -->

*Attributes defined elsewhere*

<!-- al:89 -->

-   [id](global.html#adef-id), [class](global.html#adef-class) ([document-wide identifiers](../struct/global.html#id-and-class))
-   [lang](dirlang.html#adef-lang) ([language information](../struct/dirlang.html#language-info)), [dir](dirlang.html#adef-dir) ([text direction](../struct/dirlang.html#bidirection))
-   [title](global.html#adef-title) ([element title](../struct/global.html#title))
-   [style](../present/styles.html#adef-style) ([inline style information](../present/styles.html#style-element))
-   [onclick](../interact/scripts.html#adef-onclick), [ondblclick](../interact/scripts.html#adef-ondblclick), [onmousedown](../interact/scripts.html#adef-onmousedown), [onmouseup](../interact/scripts.html#adef-onmouseup), [onmouseover](../interact/scripts.html#adef-onmouseover), [onmousemove](../interact/scripts.html#adef-onmousemove), [onmouseout](../interact/scripts.html#adef-onmouseout), [onkeypress](../interact/scripts.html#adef-onkeypress), [onkeydown](../interact/scripts.html#adef-onkeydown), [onkeyup](../interact/scripts.html#adef-onkeyup) ([intrinsic events](../interact/scripts.html#events))

<!-- al:90 -->

The [DIR](lists.html#edef-DIR) element was designed to be used for creating multicolumn directory lists. The [MENU](lists.html#edef-MENU) element was designed to be used for single column menu lists. Both elements have the same structure as [UL](lists.html#edef-UL), just different rendering. In practice, a user agent will render a [DIR](lists.html#edef-DIR) or [MENU](lists.html#edef-MENU) list exactly as a [UL](lists.html#edef-UL) list.

<!-- al:91 -->

We strongly recommend using [UL](lists.html#edef-UL) instead of these elements.

* * *

[previous](text.html)   [next](tables.html)   [contents](../cover.html#minitoc)   [elements](../index/elements.html)   [attributes](../index/attributes.html)   [index](../index/list.html)