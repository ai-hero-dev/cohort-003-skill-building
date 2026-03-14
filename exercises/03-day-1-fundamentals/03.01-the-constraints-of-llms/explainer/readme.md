Large language models aren't junior developers. They're something fundamentally weirder and more constrained than that.

Understanding these constraints is critical. Without this knowledge, you'll blame the model, the provider, or Claude Code itself when things go wrong. In reality, you're probably working against the model's nature instead of with it.

The constraints of LLMs force you to improve your codebase quality, structure your context carefully, and design feedback loops into your workflow. Get these wrong, and you'll end up with garbage output. Get them right, and Claude Code becomes a genuinely powerful coding partner.

## Steps To Complete

- [ ] Watch the video and understand the smart zone vs. dumb zone problem

The smart zone is where the model has enough attention budget to work sharply. The dumb zone is where attention relationships become strained and reasoning degrades.

![Diagram showing smart zone and dumb zone in the context window](https://res.cloudinary.com/total-typescript/image/upload/v1773479487/ai-hero-images/rvgkn2c1yrlqmqanysdk.png)

With a 200,000 token limit, the smart zone typically extends to around 80,000 tokens. Beyond 80-90% of your context window, you're in serious trouble.

Think of it like a football league where every new team has to play every other team. Adding tokens scales quadratically, not linearly.

![Visualization showing quadratic scaling of token relationships](https://res.cloudinary.com/total-typescript/image/upload/v1773479488/ai-hero-images/tnvi3azlhvft1fzfxacj.png)

- [ ] Learn why hallucinations happen and what they actually are

Hallucinations aren't bugs. They're what happens when you ask an LLM about information outside its fuzzy, compressed knowledge. The model wants to help so badly that it fills gaps with plausible-sounding nonsense.

![Diagram showing training data compressed into model parameters](https://res.cloudinary.com/total-typescript/image/upload/v1773479488/ai-hero-images/o9c03mot6uhoxartgmi3.png)

Write down three examples of hallucinations you've seen or could imagine seeing in Claude Code (inventing methods, getting API structure wrong, etc.).

- [ ] Understand why you can't use LLMs as databases

LLMs have read all of the internet's public knowledge but compressed it down to a blurry JPEG. They can't reliably recall information from their training data. The only information they see sharply is what's currently in the context window. Write down why this means you need to include documentation and code examples in your prompts instead of relying on the model's memory.

- [ ] Explore the statelessness constraint and what it means for your codebase

Every new conversation is a blank slate. Claude Code is like a new developer joining your team every 20 minutes with zero institutional knowledge.

This means your codebase quality directly determines how effective Claude Code will be. Ask yourself: is your repository friendly to new starters? Can someone get oriented quickly? Are related pieces grouped together?

- [ ] Learn about knowledge cutoff dates and their impact

The model was trained on data up to a specific date. Anything newer than that is invisible to its parametric knowledge. If your library shipped a major version after the training cutoff, the model won't know about it. This reinforces why you can't rely on the model's internal knowledge - you have to provide the information in the context window.

- [ ] Reflect on how these constraints connect

Write down how attention scaling, hallucinations, statelessness, and knowledge cutoff are all interconnected. How does managing one constraint help you manage the others? What would your workflow look like if you had to account for all four?

- [ ] Understand the 1 million token context window update

Claude recently [shipped 1 million token context windows](https://claude.com/blog/1m-context-ga) for Opus 4.6 and Sonnet 4.6. However, this doesn't change the smart zone calculation. The smart zone is still the first 80,000 to 100,000 tokens of the context window.

![Explanation of smart zone remaining at 80-100k tokens despite 1M context window](https://res.cloudinary.com/total-typescript/image/upload/v1773479489/ai-hero-images/vucexnj030dt4rosah4q.png)

What Claude has effectively done is ship a lot more dumb zone. The context window is just a limit decided by the developers based on how much they think the model can handle. While this limit will likely rise over time, the smart zone threshold remains relatively fixed for now.