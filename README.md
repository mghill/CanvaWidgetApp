The main body of the test is in the [widgetApp](widgetApp.md) markdown file. The ReadMe will serve for the discussion and meta-content.

To start off with, I have decided to present all 3 sections in the same What's New page. This is for brevity and simplicity, and could be used for internal content review. Each `Header2` section would be split into the appropriate Guide. The intro section could be removed or used as a landing page and link to each of the others, depending how the docs are structured overall.

I wasn't sure how much liberty to take about making decisions around hypothetical company terminology. For example, this sentence uses plain language similar to the notes section:
> This feature is optional and specifically approved per user group. 

You could capitalise, assuming that User Groups are a specific admin feature of the backend. Or you could say `user_groups` if they are some datastructure which supports user IDs within a team or org. I figured it wasn't necessarily hugely important which  of these I went with, but there were a few choices similar to this 

I also did not go into technical detail for a few reasons. I assumed that this was an overview, and I lacked the specific systems to draw examples from. Any bits I would throw together, such as very generic API calls or similar, would be in the realm of assumed knowledge for the readers of the relevant sections. If I was really in this company I would find some snippets to use, and do things like link to the relevant APIary or equivalent for the new system.

And, of course, I would expect to do at least one re-draft of this after it's had another set of eyes on it.

## What Went Where?

### User
- This had relativly little detail but focused on the experiential changes of the streaming frontend
- I would seek out more information about the actual differences here - I wouldn't go ahead and publish what I've got, I'd speak to the SME for this to get something more. Or to have the discussion resolve that anything further is basically a marketing team task at that point.

### Admin
- Pretty much all of the changes were worth mentioning here, but modified to full sentence explanations while preserving the technical terminology
- There was a generally less rewording from the notes, as Admin Users would understand SME terminology and want fairly to-the-point information

### API
- Basically a distilled version of the Admin section with just the parts that are relevant for third parties. 
- Even closer to the notes in wording as I would expect that the majority of API users would *not* be looking for a text-heavy description. I'm assuming this is only really going to get a glance before they click through to the specs and API docs themselves.  
