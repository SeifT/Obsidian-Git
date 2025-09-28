Reset View Icon is not intuitive

# Design
- When trying to find the topic "Retrieval Augmented Generation", it didn't appear. I should have written Retrieval-Augmented Generation.
	- Synonym & Abbreviation mapping.
	- Indexing all aliases
	- Maybe even Fuzzy Search
	- Use a better layout algorithm, like D3.js, t-SNE, or UMAP.
	- Make the hovered over dot highlighted
- Performance: It is already a bit unresponsive imo, at least on my laptop. 
	- For later, when there is a larger number of papers, use lazy loading or level-of-detail rendering.
- Provide a clear onboarding tutorial for new users, or tooltips.
- Allow for filtering papers by year, type, keywords...
- Personalized recommendations.
	- Recommended items viewed by different users. "People who viewed RAG also viewed ..."
	- perhaps through an agent. "New papers in your favorite topics last week"
- Feedback channel
- Monetized API

# Agents
- For recommendations. An agent could pop up at startup every time. New papers in your favorite topics last week.
- For organizing. "I found x different survey papers on RAG. They differed on the following."
- Have an "assistant" agent. Organize papers by relevance, help with planning a project, set reminders for follow ups.
- Implement agents with multi-step query handling.

# Big Takeaways for me:
- Optional Tutorial is needed.
- Personalized recommendations based on other user's usage is a strong feature imo.
- The platform is still a bit dry. No Agent-driven notification of new papers. 
- LLM summaries and Q&A is quite static. Agents would improve the quality of understanding of users.
- Ideally, when it comes to an Agent, we would want it to be always present. There, proactive, but also ready to be given a task "Ask the Research Agent".
	- Instructions such as "extract the papers before/after the year xxxx", or "extract the citations of all of these papers"....
- Allow for filtering papers by year, type, keywords...

# Nitpicks
- The name of the button "Explore Deeper" is not very clear on what it will do. Maybe we can change the name of add a tooltip which describes it when hovering over it.
- In "Explore Deeper" view, yellow dots are too cluttered and bunched up together.
- Blue "click to view paper details" indicates that this text is clickable. We don't really need that. Especially since it is NOT clickable.
- Design the dots so they signal that they are clickable. Instead of the blue "click to view paper details" text, which doesn't serve a purpose (It actually confused me).
- Yellow on Green is not the best for accessibility. Most common color blindness deficiency is with yellow and green.


Helping tool vs solving tool spectrum