---

title: first blog post, or <br> <i>"why this website looks so simple"</i> 
permalink: /_pages/blog/2026_06_14_first_blog_post/ 
layout: single
author_profile: true
toc: true

---

# Preface

When I decided to show my friends this website, the most common reaction was: *why it's so... simple* ?  
And I totally get it, nowadays the frontend website standards are pretty high: lots of images that seemingless transition into eachother,
cute animations, and serious design choices that make websites look like modern art galleries.  
Don't get me wrong, lots of compliments to those working on them behind the scene.  

# Core thesis 

What I feel like it's left behind in building your own website is the **purpose**: 

- Is it a style exercise? 
- You want to show off something? 
- You want a space to discuss your ideas? 
- Or you just like the idea of having your online presence not limited to social medias?  

This is the very single, fundamental decision that dictates the development and maintenance of your website.  
For me, the main scope was **having a single space to store my personal project, work experiences and off topics**.  
I personally couldn't care less about web development *(sorry not sorry)*, neither about having a flashing website to show off. 

# My Software Stack 

This is all the things used to create, host and deploy my website:

- GitHub Pages: deployment and hosting
- Jekyll: website building
- Minimal Mistakes Theme: a Jekyll theme 
- VSCodium: text editor 

We are going to need this later.

---

# Argument 1: Simplicity 

The **KISS**, *Keep It Simple, Stupid!* principle is very well-known in the software development world, 
no matter the specific field of work.  
If you have the chance to obtain the same result with the same performance, and you need to choose between 
two implementations, you *usually* choose the simpler one. Obviously, also maintenability and scaling should be 
taken into account, but for the sake of the example we can assume they are equal.  
There are several reasons for such decision, but we can summarize them down, more or less, to the followings: 

- Simpler implementations are, *usually*, less bug-prone 
- Simpler implementations are, *usually*, easier to understand 
- Simpler implementations are, *usually*, less prone to future refactoring and changes 
- Simpler implementations are, *usually*, faster to implement 

Given these reasons, it feels natural to prefer simple implementations over more complex and powerful implementations.  
If I haven't convinced you yet, try to answer to the question:  
***How often do I need this specific thing that something simpler can't make?***  

# Argument 2: Clarity & Effectiveness 

Communication, online and offline, can be roughly decomposed into **clarity** and **effectiveness**.  \\
You want to be able *transmit* the message succesfully but also make it *understandable* once it reaches its audience. 

- Your message could be very clear, but if it's not effective, it doesn't have any effect. 
- Your message could be very effective, but not clear, your interlocutor won't understand **why** 
you communicated with him in the first place 
- Your message could be neither clear nor effective, and it's just jibberish. 

It's pretty easy to see that we are striving for both clarity **AND** effectiveness.  
Complex websites, with lots of transitions, effects, etc. maybe look awesome, but unless done *professionally*, 
there's a very high risk of lacking clarity. 
The website is cool, but if I don't find what I'm looking for, I'm just going to close it. \\
On the same wavelength, effectiveness should be reached. To improve effectiveness, we should measure it, somehow. 
It's difficult to measure effectiveness without using user data, % of conversions, etc. \\
But this is not an e-commerce, and it would be non-sense. 
We achieve effectiveness in the moment a recruiter asks about something specific inside this website. \\
Before that moment, I must admit, other than being as clear as possible, being effective is not so trivial to obtain. 

# Argument 3: Speed of Development 

Complex things require time to be done properly. Especially complex **software**. 
The time between analyzing, designing, developing, testing and deploying is in *order of magnitude *
bigger than what it's required to desing, develop, test and deploy something simpler.  
When it comes to web development, I feel this gap is well-known and pretty understandable.  
That's why front-end frameworks exists, but even them have a learning curve. And I didn't want to **waste** time 
in learning something that is not of my interest nor useful for my future studies.  
And here's where Markdown makes its own show. A "language" I already know, easy and fast to type, powerful enough for my 
purposes.  
Among the different choices, such as Notion, I still preferred to choose Jekyll + GitHub Pages.  
I still wanted to mess around with repositories and terminal commands!  

# Counter Argument 1: AI

*You couldn't care less, so why not just use AI to build all the website for you and just type?*  
Good point, pretty good.  
Let's dive into it. 

## Doing it yourself just for the sake it 

Sounds kinda dumb, but I want to be as trasparent as possible: I had no deadline for when the 
website should've been online. Neither I had someone else's interest into consideration for this.  
Yes, I still cared about speed of development, but as the effort required to make the website working 
wasn't overwhelming, neither the deadline strict, why not just working on it by myself to 
**feel better**?  
Before pursuing my degree, typing on a keyboard and making my computer do *beep boop* was my **fun** activity.  
University studies leave me a fraction of the free time I used to have in previous years, so 
doing something just for fun it's something that doesn't happen so often.  
Why not **mix business with pleasure?**

## Implications of using AI 

I don't have my own GPU rack at home. Neither my Framework 13 can run LLMs on a dime.
If I want to use AI, I need to revert to **companies**, such as Google, OpenAI, Anthropic, etc.  
This implies I don't have ownership of my data, and this just feeds data into the machine of 
the digital identity that these data providers make.  
Every step, even if small, done to strive away from such data harnessing, it's a step towards 
**online privacy**.  
Even if the prompt could've been just "make me a cool portfolio", and wouldn't have had so 
big complications, I preferred to cheap out :D 

## Use your brain 

Yes, AI can write code, very well, *very likely even better than me*, and the same goes for websites.  
But AI **doesn't** have a brain. I **do**.
And guess what? Not using your brain **sucks**.  
Because when you are in the field, whatever field of your life, professional or not, 
you won't always have the option to "ask for a second opinion" to ChatGPT.  
And if you don't have your brain to work with, what's the difference between you and a plant? 

# Counter Argument 2: "Real" Providers 

*If you wanted to have your own site so badly, why not using hosting platform or no-code options, such as Notion, Wordpress, etc.?*  
Again, fair enough. I totally get it. Let's see why I decided to diverge from some very well-known options.

- ## Notion Site
  - **Pros**: very cool, Markdown-oriented, better looking.  
  - **Cons**: up to 5MB uploads, which means that videos are a big no-no, completely no-code 
- ## Wordpress
  - **Pros**: easy to setup, very powerful, lots of ready to use templates
  - **Cons**: free plan a bit limiting, completely no-code, heavy
- ## Webflow
  - **Pros**: the most gorgeous choice, incredibly detailed 
  - **Cons**: speed of development, no code, everything is about images

Don't come at me for missing your personal choice.
I just wanted to give out **some** feasible choices that I was aware of
before deciding to build this website.  
I think the pattern it's pretty easy to spot: **if it's free, it has limitations, either in the speed of development, 
in the content upload, or in the learning curve**.  
Most of these providers don't let me do what I was stressing on  
*"Doing it yourself for the sake of doing it"*.  
Therefore, it's clearer why a simple pair such as Jekyll + GitHub Pages was an overall better trade-off, a learning curve not too hefty, **enough** freedom of choice, and nothing overly-complicated just for the sake of having the *coolest*.  
I want to stress **trade-off**.  
Because in engineering the perfect solution never exists, 
there are *only* trade-offs, which change upon the context and constraints.

# Wrapping up 
I've briefly explained the software stack used to develop & deploy this website, 
gave arguments and counter-arguments for such decisions, 
and, hopefully, made you understand why I made such choices.   
I hope this to be the first of many-to-come blog posts.  
It's not the best blog post you will ever read, but everyone has to 
start **somewhere**. 
Cheers!  
Benedetto.  
*Ad maiora*
