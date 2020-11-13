---
Title: About
Description: About this page.
icon: fas fa-user
# hidden: true
---

About this page.
==================
* This is a description of how this page is built and what i have done. This is the first time is use scss and i have limited experience with css from the htmlphp course.

I have used a different icons from fontawesome, both in the menu and the footer. I realise the icons in the header menu ain't that descriptive but that's a future problem. 

"font-family: 'Roboto', sans-serif;" is the font i chose to use, imported from fontawesome also. Im planning on picking another for the Titles and headlines.

I utilised a variable set in shared/scss/variables.scss thats imported in shared/scss/base.scss which is imported in style.scss to set the background color throughout the page.

The sass watch auto-compiler is a very useful tool i have used to save time. It eliminates the need of running the "npm run style" command and makes the changes in your scss/css files as soon as you save.

The mobile page looks alright except for the picture is a little bit compressed on my phone screen but i like the menu. Although i would like the buttons to line up horizontally instead of the way they look at the moment i'm writing this. I'll look into it if i have time.

# Here are some examples of cool stuff you can do:
```
<!DOCTYPE html>
<html>
    <head>
        <title>This is a Title in HTML</title>
    </head>
    <body>
        <p>I don't know what to write i just like it.</p>
    </body>
</html>
```

Tables
-----

<fieldset>
    <legend>Legend</legend>
    <label>Label</label>
    <input type="checkbox"/>
    <input type="checkbox" checked="checked"/>
    <input type="radio"/>
    <input type="radio" checked="checked"/><br/>
    <input type="text" value="This is a textbox for input."/>
    <input type="password" value="password"/><br/>
    <input type="submit" value="Submit"/>
    <input type="reset" value="Reset"/>
    <input type="button" value="Button (Input)"/>
    <button>Button</button><br/>
    <textarea>How cool is this thing, you can pull it out and pick the size yourself!</textarea><br/>
    <select>
        <option>Rolldown menu</option>
        <option>Option 1</option>
        <option>option 2</option>
    </select><br/>
    <select multiple="multiple">
        <option>Open menu</option>
        <option selected="selected">Option 1</option>
        <option>Option 2</option>
        <option>Option 3</option>
    </select>
</fieldset>
