--- 
title: Global typographic styles suck
date: 2012/05/06
---

I hate global styles. I really do. For every line you add to an element selector globally you'll write dozens of lines of code removing that one style later down the road. There's a particular technique that I've been advocating a lot over the past year at work - removing all typographic styles from the global scope. Doing this allows you to remove hundreds of lines of code. 

Traditionally, we'll apply typographic styles to elements like strong, em, p, ul, h1, h2, h3 etc, in the global scope. We are adding these styles to the elements globally. We think to ourselves "we're using the cascade!" and wrongly thinking that we're saving lines of code in the long run. 

I think we need to rethink this approach.

**In my stylesheets I remove all global typographic styles from every element**. Instead I set these properties to inherit so that all the common elements on the page look the same way. List items no long have padding or bullets, links are no longer bold and add an underline on hover, headings no longer have margin and inherit their size and colour. 

It sounds a lot like the global reset that has been around in various forms for the past 10 years. The difference is that I only target typographic elements. **I've moved all of these styles into a class appropriately named** <code>.copy</code>. Now I can apply this class to any block that I expect to behave like a block of formatted copy. 

[Here's an example of a copy class](https://github.com/anthonyshort/Compass-Template/blob/master/media/screen/styleguide/_copy.scss) that I've used on past projects and [this is the reset file](https://github.com/anthonyshort/stitch-css/blob/master/stylesheets/stitch/_reset.scss) that sets text elements to inherit styles.

**The copy is a now a module.** I can create variations of these copy styles for user generated content or modify styles within other modules (like a sidebar block).

Removing all text styles from the global scope allows me to create buttons and navigation elements without needing to remove previous styles. I can turn an anchor into a button and I won't have to remove the underline on the links and change their font weight. I don't have to remove the bullet from the list items or remove the italic text from the emphasis tag. Headings within modules no longer need code to remove the margin so that they sit inside that box correctly.

Combining this approach with other modular techniques allows you to write selectors that only include the styles that they really need. Forget those lines of code that exists just to remove styles they've inherited from the global scope. For me global styles are now just as evil as global variables. Why would you globally style headings and links the way they appear in a single place? 

I've found it difficult to explain why this approach is beneficial. It's difficult to give code examples. I'd probably have to build a site with and without global typographic styles to show the difference. Even then it doesn't prove just how much more maintainable the stylesheets become.

If you don't believe me then give this a go on your next project. You'll never go back.

You can [comment on this post over on Github](https://github.com/anthonyshort/anthonyshort.me/issues/4).