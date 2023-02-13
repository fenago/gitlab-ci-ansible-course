Basic writing and formatting syntax
===================================


Create sophisticated formatting for your prose and code on Gitlab with
simple syntax.


Headings
---------------------------------------------------

To create a heading, add one to six [\#] symbols before your
heading text. The number of [\#] you use will determine the size
of the heading.

    # The largest heading
    ## The second largest heading
    ###### The smallest heading

![Rendered H1, H2, and H6
headings](./images/headings-rendered.png)



Styling text
-----------------------------------------------------------

You can indicate emphasis with bold, italic, strikethrough, subscript,
or superscript text in comment fields and `.md` files.

![](./images/1.png)


Quoting text
-----------------------------------------------------------

You can quote text with a [\>].

    Text that is not a quote

    > Text that is a quote

![Rendered quoted text](./images/quoted-text-rendered.png)



Quoting code
-----------------------------------------------------------

You can call out code or a command within a sentence with single
backticks. The text within the backticks will not be formatted. You can
also press the [Command]+[E] (Mac) or [Ctrl]+[E]
(Windows/Linux) keyboard shortcut to insert the backticks for a code
block within a line of Markdown.

    Use `git status` to list all new or modified files that haven't yet been committed.

![Rendered inline code
block](./images/inline-code-rendered.png)

To format code or text into its own distinct block, use triple
backticks.

    Some basic Git commands are:
    ```
    git status
    git add
    git commit
    ```

![Rendered code block](./images/code-block-rendered.png)

If you are frequently editing code snippets and tables, you may benefit
from enabling a fixed-width font in all comment fields on Gitlab.

Supported color models
----------------------------------------------------

In issues, pull requests, and discussions, you can call out colors
within a sentence by using backticks. A supported color model within
backticks will display a visualization of the color.

    The background color should be `#ffffff` for light mode and `#0d1117` for dark mode.

![Rendered supported color
model.](./images/supported-color-models-rendered.png)

Here are the currently supported color models.

![](./images/2.png)


**Notes:**

-   A supported color model cannot have any leading or trailing spaces
    within the backticks.
-   The visualization of the color is only supported in issues, pull
    requests, and discussions.


Lists
---------------------------------------------

You can make an unordered list by preceding one or more lines of text
with [-], [\*], or [+].

    - George Washington
    * John Adams
    + Thomas Jefferson

![Rendered unordered
list](./images/unordered-list-rendered.png)

To order your list, precede each line with a number.

    1. James Madison
    2. James Monroe
    3. John Quincy Adams

![Rendered ordered list](./images/ordered-list-rendered.png)

### Nested Lists

You can create a nested list by indenting one or more list items below
another item.

To create a nested list using the web editor on Gitlab or a text editor
that uses a monospaced font, like `Visual Studio Code`, you can align your list visually.
Type space characters in front of your nested list item, until the list
marker character ([-] or [\*]) lies directly below the first
character of the text in the item above it.

    1. First list item
       - First nested list item
         - Second nested list item


**Note**: In the web-based editor, you can indent or dedent one or more
lines of text by first highlighting the desired lines and then using
[Tab] or [Shift]+[Tab] respectively.


![Nested list with alignment
highlighted](./images/nested-list-alignment.png)

![List with two levels of nested
items](./images/nested-list-example-1.png)

To create a nested list in the comment editor on Gitlab, which doesn\'t
use a monospaced font, you can look at the list item immediately above
the nested list and count the number of characters that appear before
the content of the item. Then type that number of space characters in
front of the nested list item.

In this example, you could add a nested list item under the list item
`100. First list item` by indenting the nested list item a minimum of
five spaces, since there are five characters (`100. `) before
`First list item`.

    100. First list item
         - First nested list item

![List with a nested list
item](./images/nested-list-example-3.png)

You can create multiple levels of nested lists using the same method.
For example, because the first nested list item has seven characters
(`␣␣␣␣␣-␣`) before the nested list content `First nested list item`, you
would need to indent the second nested list item by seven spaces.

    100. First list item
         - First nested list item
           - Second nested list item

![List with two levels of nested
items](./images/nested-list-example-2.png)


Task lists
-------------------------------------------------------

To create a task list, preface list items with a hyphen and space
followed by `[ ]`. To mark a task as complete, use `[x]`.

    - [x] Complete PR Review
    - [ ] Add delight to the experience when all tasks are complete :tada:

Using emoji
---------------------------------------------------------

You can add emoji to your writing by typing `:EMOJICODE:`.

`:+1: This PR looks great - it's ready to merge!`

![Rendered emoji](./images/emoji-rendered.png)

Typing [:] will bring up a list of suggested emoji. The list will
filter as you type, so once you find the emoji you\'re looking for,
press **Tab** or **Enter** to complete the highlighted result.

Paragraphs
-------------------------------------------------------

You can create a new paragraph by leaving a blank line between lines of
text.

Footnotes
-----------------------------------------------------

You can add footnotes to your content by using this bracket syntax:

    Here is a simple footnote[^1].

    A footnote can also have multiple lines[^2].  

    You can also use words, to fit your writing style more closely[^note].

    [^1]: My reference.
    [^2]: Every new line should be prefixed with 2 spaces.  
      This allows you to have a footnote with multiple lines.
    [^note]:
        Named footnotes will still render with numbers instead of the text but allow easier identification and linking.  
        This footnote also has been made with a different syntax using 4 spaces for new lines.

The footnote will render like this:

![Rendered footnote](./images/rendered-footnote.png)


**Note**: The position of a footnote in your Markdown does not influence
where the footnote will be rendered. You can write a footnote right
after your reference to the footnote, and the footnote will still render
at the bottom of the Markdown.

Footnotes are not supported in wikis.


Hiding content with comments
----------------------------------------------------------------

You can tell Gitlab to hide content from the rendered Markdown by
placing the content in an HTML comment.

    <!-- This content will not appear in the rendered Markdown -->

Ignoring Markdown formatting
----------------------------------------------------------------

You can tell Gitlab to ignore (or escape) Markdown formatting by using
[\\] before the Markdown character.

`Let's rename \*our-new-project\* to \*our-old-project\*.`

![Rendered escaped
character](./images/escaped-character-rendered.png)

