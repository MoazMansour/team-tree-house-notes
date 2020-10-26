# HTML and CSS Basics

Every thing on the web uses HTML and CSS to some degree.

**HTML:**
HyperText Markup Language, a set of tags we use to describe the structure of web pages.

**CSS:**
Cascading Style Sheets, a language used to describe how an HTML element should look when displayed in a browser.

## HTML

-   All of the website content is wrapped in HTML tags.
-   Most of those tags have an opening tag and a closing tag.
-   Each HTML tag can have attributes on them.
-   Attributes give the browser more information about how the tag should work or look.

### Web Page Structure

-   You can think of all the different parts of your webpage as a series of boxes that lives within one other.
-   The outer most part is HTML. That contains all the information about your webpage.
-   Inside HTML are two more boxes; `<head>` and `<body>`.
-   `<head>` contains a lot of behind the scenes information that people won't see, but it is important for the browser to display your pages.
-   `<body>` box contains everything you see in the browser.

### Doctype

-   Everything within your HTML is nested within the `<html>` tag.
-   The only thing that sits outside of the `<html>` tag is the doctype.
-   The doctype: `<!doctype html>` let's the browser know that you are asking it to display an HTML document.
-   It always sits on the top of your html document.
-   It desn't require a closing tag and nothing is nested inside of it.

### Head Tag

-   Contains invisible info.
-   Such as the title of the page `<title>`, which will display in search engine results and browser tabs.
-   It also includes links to other documents that the browser needs to display properly like CSS. tagged by `<link>`
-   You also link to JavaScript files within the head tag.
-   It also contains `<meta>` tags, they provide information that is used by browsers and search engines.

### Body Tag

-   The code that's visible in the browser must be nested inside the body tags.
-   Many web designers divide the page into 3 sections; `<header>`, `<main>`, and `<footer>`.
-   Header often contains introductory information. It can also contains the site navigation menu.
-   Navigation menu is mainly a list of links to other pages in the site.
-   The `<main>` section contains the bulk of the information and content we want to share with the world.
-   The `<footer>` usually contains things like copyrights information and social media links.

### Tags

#### Heading Tags:

-   An h1 tag is part of the set of HTML heading tags that are numbered from 1 to 6.
-   1 being the most important title on your page, and six being for the smallest subheading.
-   Each heading tag comes with some default CSS styles and that controls how big the text appears.

#### Image tag:

-   The image tag; `<img>` could have three attributes: `src=`, `alt`, `class`.
-   The `src=` attribute points to a file path. To the location of the image file on your site.
-   You can also link to an absolute url. A full web address that links to an image that's outside of your website.
-   `alt=` is short for alternative text.
-   You should always put a precise descfription of your image into your alt attribute.
-   This is the text your users will see if the image is broken. It is also used by search engines too.
-   It enhances accessibilty for the visually impaired.
-   The `<img>` tag doesn't have a closing tag. It is called a self closing tag or empty elements.

#### Paragraphs tags:

-   Paragraphs tags are pretty much what they sound like. They are used to split up text into paragraphs.
-   `<p>` creates a space between text because it comes with a default margin value which you can control using CSS.

#### Link Tag:

-   An anchor tag `<a>` is how we create clickable links.
-   The `href` attribute is always used with the link tag.
-   `href` stands for the HyperText reference. That's how you tell the browser where we want it to go.
-   To reference to a different place in a page you can do something similar to this
        <a href="#top">link</a>
-   If you want the browser to open a new tab when a user clicks on a link, you can add another attribute called `target="_blank"`

#### List tag:

-   You can create a list with one of two tags: `<ul>` or `<ol>`
-   `<ul>` stands for unordered list.
-   `<ol>` stands for ordered list.
-   To spearate the items in the list, you need to nest another tag inside the list an `<li>` tag.
-   `<li>` stands for list item.

## CSS

-   Select the corresponding HTML elements or tags.
-   Then between the curly braces, put your style instructions.

### Classes

-   Classes are one of the ways we can tell our CSS that this is the element I want to style or fomrat in some way.
-   
