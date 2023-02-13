Quickstart for writing on GitHub
================================

In this lab, we will cover following topics:

- Creating or editing your profile README
- Adding an image to suit your visitors
- Adding a table
- Adding a collapsed section
- Adding a quote
- Adding a comment
- Saving your work

Learn advanced formatting features by creating a README for your GitHub
profile.


Creating or editing your profile README
-----------------------------------------------------------------------------------

Your profile README lets you share information about yourself with the
community on GitHub.com. The README is displayed at the top of your
profile page.

If you don\'t already have a profile README, you can add one.

1.  Create a repository with the same name as your GitHub username,
    initializing the repository with a `README.md` file.
    
2.  Edit the `README.md` file and delete the template text (beginning
    `### Hi there`) that is automatically added when you create the
    file.

If you already have a profile README, you can edit it from your profile
page.

1.  In the upper-right corner of any GitHub page, click your profile
    photo, then click **Your profile**.

2.  Click the next to your profile README.

    ![Screenshot of a profile page, with the pencil icon highlighted
    next to the profile
    README](./images/edit-profile-readme.png)

Adding an image to suit your visitors
-------------------------------------------------------------------------------

You can include images in your communication on GitHub. Here, you\'ll
add a responsive image, such as a banner, to the top of your profile
README.

By using the HTML `<picture>` element with the `prefers-color-scheme`
media feature, you can add an image that changes depending on whether a
visitor is using light or dark mode.

1.  Copy and paste the following markup into your `README.md` file.

    
```
<picture>
 <source media="(prefers-color-scheme: dark)" srcset="YOUR-DARKMODE-IMAGE">
 <source media="(prefers-color-scheme: light)" srcset="YOUR-LIGHTMODE-IMAGE">
 <img alt="YOUR-ALT-TEXT" src="YOUR-DEFAULT-IMAGE">
</picture>
```
    

2.  Replace the placeholders in the markup with the URLs of your chosen
    images. Alternatively, to try the feature first, you can copy the
    URLs from our example below.

    -   Replace `YOUR-DARKMODE-IMAGE` with the URL of an image to
        display for visitors using dark mode.
    -   Replace `YOUR-LIGHTMODE-IMAGE` with the URL of an image to
        display for visitors using light mode.
    -   Replace `YOUR-DEFAULT-IMAGE` with the URL of an image to display
        in case neither of the other images can be matched, for example
        if the visitor is using a browser that does not support the
        `prefers-color-scheme` feature.

3.  To make the image accessible for visitors who are using a screen
    reader, replace `YOUR-ALT-TEXT` with a description of the image.

4.  To check the image has rendered correctly, click the **Preview**
    tab.


### Example

    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://user-images.githubusercontent.com/25423296/163456776-7f95b81a-f1ed-45f7-b7ab-8fa810d529fa.png">
      <source media="(prefers-color-scheme: light)" srcset="https://user-images.githubusercontent.com/25423296/163456779-a8556205-d0a5-45e2-ac17-42d089e3c3f8.png">
      <img alt="Shows an illustrated sun in light mode and a moon with stars in dark mode." src="https://user-images.githubusercontent.com/25423296/163456779-a8556205-d0a5-45e2-ac17-42d089e3c3f8.png">
    </picture>

### How it looks

![Screenshot of the Preview tab in light mode, with an image of a
smiling sun displayed](./images/lightmode-image-example.png)

Adding a table
------------------------------------------------------------

You can use Markdown tables to organize information. Here, you\'ll use a
table to introduce yourself by ranking something, such as your most-used
programming languages or frameworks, the things you\'re spending your
time learning, or your favorite hobbies. When a table column contains
numbers, it\'s useful to right-align the column by using the syntax
`--:` below the header row.

1.  Return to the **Edit file** tab.

2.  To introduce yourself, two lines below the `</picture>` tag, add an
    `## About me` header and a short paragraph about yourself, like the
    following.

        ## About me

        Hi, I'm Mona. You might recognize me as GitHub's mascot.

3.  Two lines below this paragraph, insert a table by copying and
    pasting the following markup.

    
```
| Rank | THING-TO-RANK |
|-----:|---------------|
|     1|               |
|     2|               |
|     3|               |
```

4.  In the column on the right, replace `THING-TO-RANK` with
    \"Languages,\" \"Hobbies,\" or anything else, and fill in the column
    with your list of things.

5.  To check the table has rendered correctly, click the **Preview**
    tab.


### Example

    ## About me

    Hi, I'm Mona. You might recognize me as GitHub's mascot.

    | Rank | Languages |
    |-----:|-----------|
    |     1| Javascript|
    |     2| Python    |
    |     3| SQL       |

### How it looks

![Screenshot of the Preview tab, showing an \"About me\" heading and a
rendered table with a list of
languages](./images/markdown-table-example.png)

Adding a collapsed section
---------------------------------------------------------

To keep your content tidy, you can use the `<details>` tag to create an
expandible collapsed section.

1.  To create a collapsed section for the table you created, wrap your
    table in `<details>` tags like in the following example.

    
    HTML
        <details>
        <summary>My top THINGS-TO-RANK</summary>

        YOUR TABLE

        </details>
    

2.  Between the `<summary>` tags, replace `THINGS-TO-RANK` with whatever
    you ranked in your table.

3.  Optionally, to make the section display as open by default, add the
    `open` attribute to the `<details>` tag.

        <details open>

4.  To check the collapsed section has rendered correctly, click the
    **Preview** tab.

### Example

    <details>
    <summary>My top languages</summary>

    | Rank | Languages |
    |-----:|-----------|
    |     1| Javascript|
    |     2| Python    |
    |     3| SQL       |
      
    </details>

### How it looks

![Screenshot of the Preview tab, with a collapsed section called \"My
top languages\" marked by a dropdown
arrow](./images/collapsed-section-example.png)

Adding a quote
------------------------------------------------------------

Markdown has many other options for formatting your content. Here,
you\'ll add a horizontal rule to divide your page and a blockquote to
format your favorite quote.

1.  At the bottom of your file, two lines below the `</details>` tag,
    add a horizontal rule by typing three or more dashes.

        ---

2.  Below the `---` line, add a quote by typing markup like the
    following.

        > QUOTE

    Replace `QUOTE` with a quote of your choice. Alternatively, copy the
    quote from our example below.

3.  To check everything has rendered correctly, click the **Preview**
    tab.

### Example

    ---
    > If we pull together and commit ourselves, then we can push through anything.

    — Mona

### How it looks

![Screenshot of the Preview tab, with an indented quote below a thick
horizontal line](./images/markdown-quote-example.png)

Adding a comment
----------------------------------------------------------------

You can use HTML comment syntax to add a comment that will be hidden in
the output. Here, you\'ll add a comment to remind yourself to update
your README later.

1.  Two lines below the `## About me` header, insert a comment by using
    the following markup.

        <!-- COMMENT -->

    Replace `COMMENT` with a \"to-do\" item you remind yourself to do
    something later (for example, to add more items to the table).

2.  To check your comment is hidden in the output, click the **Preview**
    tab.

### Example

    ## About me

    <!-- TO DO: add more details about me later -->

Saving your work
----------------------------------------------------------------

When you\'re happy with your changes, save your profile README by
clicking **Commit changes**.

Committing directly to the `main` branch will make your changes visible
to any visitor on your profile. If you want to save your work but
aren\'t ready to make it visible on your profile, you can select
**Create a new branch for this commit and start a pull request**.

![Screenshot of the \"Commit changes\"
section](./images/readme-commit-changes.png)
