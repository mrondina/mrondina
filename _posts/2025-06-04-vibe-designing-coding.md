---
title: "Vibe Designing + Code with Claude"
subtitle: "matching my vibe coding to my designs"
summary: "Documenting how I've been learning to do my usual design and vibe coding the components for production"
client: ""
tools: ""
date: 2025-06-04 00:00:00
image: "/images/claude-vibing-banner1.png"
---

## Vibe Coding Design Components
This week, I was working on sprucing up my portfolio; a static site built in Jekyll and hosted via Github Pages. In this article, I'm going to share my full process for prompting from the finished, or nearly finished design into a Jekyll-ready component.

## Design Process Component
One element that was missing from my case studies was an overview of my design process. As I review each of my projects, I may end up having a few versions of these components depending on product maturity, but I decided to start with a case study that was very design centered.

![](/images/design-process-final.png)

This is my finished design, and there is some complexity in the styles, so let's get into the prompts.

### Starting Prompt
I decided to write all the prompts myself instead of using Claude to create the prompts. I have found that the AI generated prompts are usually a lot more detailed and complex. I wanted to have more control over the process.

#### Context Matters
I shared a screenshot of the final design withing the prompt, a screenshot of my color palette, and 3 of my sites Sass files for color, variables and base styles. The first prompt is below.

> Act as an expert front-end dev in Jekyll static sites. Create a component that follows the color styles of the branded site, used Tablericons for its iconography and is responsive across wide, desktop, tablet and mobile. Match the provided design image as much as possible. I've included Sass files for reference to colors, gradients, and global variables

![](/images/prompt-01-result.png)

The result wasn't as bad as I was expecting. Some clear issues are present, like the horizontal line, but it was a good starting point. So with that, I made some specific changes.

My objective was to control the output and make steady progress, so I kept the following prompts, more focused. I worked first on the heading for the section

> Let's make some visual adjustments:
> the main header, "Design Process" and the subheading should be inline, with a "|" between them. The size for this breakpoint of the 'Design Process' title should be 60px at this resolution "wide"

![](/images/prompt-02-result.png)

### More Specificity, Better Results
I then wanted to tackle the colors of the process boxes, the height and text within each. The design served as my main reference, giving me specific details on height and color to create a focused prompt.

> This is better, now let's work on the boxes around the main sections of the process, ie "DISCOVERY, 'DEFINITION', 'DESIGN WORKSHOP', DEVELOPEMENT
> These boxes are 48px high with a corner-radius of 11, and the text should have an icon to the left that is sized to fit no bigger than 40px
> the icons are as follows:
>Discovery - compass
>Definition is a document with lines
>Design Workshop is an eye with a small pencil
>Devlopment is </> icon
>These should all be line icons
>The boxes around the process title text is liner, from left to right:
>#B66BE5, #FC8C5C

![](/images/prompt-03-result.png)

This was progress in the right direction, but it took my gradient as a fill, not a stroke. I should have been more clear with the gradient, that it applied to the stroke, not fill. Sometimes you get what you ask for, and what you don't gets filled in with something you don't want.

The next prompt was very simple, I continue with the stroke change and kept it deliberately vague, relying on Claude's memory to see how well it would understand

>the process step boxes should have a fill of #1E2740 and the stroke is the gradient

![](/images/prompt-04-result.png)

I am not completely sure what happened on the corners, but I still felt like the progress was good - always in the right direction. So far, I've not had the "one step forward, two back" scenario.

### Ask and You Will Receive
The prompt following was literally just a question. The result had me so confused, I was left wondering how it had rounded and squared corners.

>does the gradient on the stroke not work with the rounded corners?

The response was just so classicly LLM 
>You're absolutely right! border-image doesn't work with border-radius - it creates square corners. Let me fix this by using the pseudo-element approach which will properly maintain the rounded corners:

![](/images/prompt-05-result.png)

Looking much better. I added in a few more adjustments before moving to the icons, which, as you'll see was not as straight forward as I thought it would be.

>Let's make the following adjustments:
>1. remove the horizontal line cutting through the process step details
>2. adjust the bullets in the bulleted list to be dash lines
>3. adjust the width of the process steps to enable the Excellence check to fit in this breakpoint
>4. make the excellence check a rounded square with the same colors and corner-radius as the process steps

I moved the Excellence Check to the right step in the process as well and tried to fix the unordered list as well.

>let's move the excellence check between the design workshop and development steps. 
>For the process details, wrap the <ul> in a container that can have a dashed border line with the appropriate color and 1px wide

![](/images/prompt-06-result.png)

>great! adjust the border on the process steps to only be on the left side

![](/images/prompt-08-result.png)

Looking much better!

### Fighting Over Images and Icons
Icon libraries have been around so long, I thought it would be the easiest adjustment to vibe code, but it proved to be much more difficult than I expected. Over the next five prompts, I tried unsuccesfully to get Claude to include my custom icon for the Excellence Check, but nothing I tried worked. I even tried providing the documentation from taber licons, but Claude was never able to pull any icons from their API. I considered this an easy fix once working fully in VSCode, but still disappointing to say the least.

My favorite version of this back and forth was when I provided the PNG to Claude and the following prompt:

>One more visual adjustment, let's add this .png into the Excellence Check step and make the excellence check text uppercase

The result was Claude attempting to convert the PNG to an SVG with some...interesting results.

![](/images/prompt-09-result.png)

My final adjustment was to the line separationg the Title from the subtitle.

> design process title, the "|" that separates the title from subtitle, should be white, taller and thinner

![](/images/prompt-10-result.png)

## Takeaways
My final prompt as to vibe write the conclusion to this article, curious what Claude would provide.

My prompt (I was getting lazier and lazier as the length of time it took to write this went on).

>I've written a blog post about my work prompting UI elements. Review the blog post and then, in my own voice with the right phrasing, and copy style, create the final "Key Takeaways" concluding the blog. Provide your response in markdown.

#### Claude's Response
After going through this entire process, I've learned a few things about vibe coding with Claude that I wish I'd known at the start.

**Context is everything.** Throwing screenshots, color palettes, and Sass files at Claude from the beginning made a massive difference. The first result wasn't perfect, but it was surprisingly close to what I wanted. Without that context, I'd probably still be wrestling with basic styling decisions.

**Be specific about gradients and strokes.** When I said "linear gradient from left to right," Claude interpreted that as a fill instead of a stroke. One vague prompt cost me an extra iteration. The more precise I was about exactly where colors should go, the better the results.

**Icons are still a pain point.** This was honestly the most frustrating part of the entire process. Even with documentation and PNG references, Claude couldn't pull icons from Tabler's library consistently. It's something I'll need to handle manually in VSCode, but knowing that upfront would have saved me five failed prompts.

**Small, focused prompts work better than big asks.** Instead of trying to fix everything at once, breaking changes into single adjustments kept me moving forward. I never hit that dreaded "one step forward, two back" scenario that usually kills my momentum.

**Sometimes just asking a question gets you the answer.** My favorite moment was when I simply asked "does the gradient on the stroke not work with rounded corners?" Claude immediately understood the issue and fixed it with a pseudo-element approach. Sometimes the AI knows more about CSS quirks than I do.

The biggest win here wasn't the final component—it was learning how to communicate design intent effectively to Claude. With better prompting, I can get 80% of the way to a production-ready component before I even open my code editor. That's a game changer for my workflow.