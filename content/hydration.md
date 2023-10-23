+++
title = "What the f*ck is hydration? And how it almost ruined a hackathon for me"
date = 2023-10-23

[taxonomies]
categories = ["Frontend", "Guides"]
+++

The modern state of frontend is a total disaster. Frontend has been my strongest side for 4 years now, yet it still makes me insecure whenever I need it the most.

<!-- more -->

---

Every day I get to wake up in fear of opening YouTube and seeing Fireship drop a new video about a new frontend framework that "solves everything". Of course, after spending my dear time for the 100th time by trying it out I understand that my dear time is gone, and I should go back to plain HTML/CSS.

I've got plenty frameworks under my belt I could use in different occasions and my personal go-to has always been Next.js it has a huge community support, so there's always another guy that's already had the same problem as me. I've never had issues with Next.js and that's a framework I've trusted for very long and it never fails to deliver. But I was participating in a hackathon, so naturally I had to think of a challenge for myself. Here's how it went:

![SDK Dapp frameworks](/sdk-dapp.png)

This is 18 days into the hackathon, 12 days left 'till submission. You can't even imagine how frustrating it feels to have spent the majority of time practicing skills in a single field and then realize you don't know shit.

<!-- For context `sdk-dapp` is a library used for building Dapps(Decentralized applications) that interact with Multiversex, I mean, MultiversX blockchain. The library exposes different React components and contexts which is, uhm, bit odd. That means that by the nature of it, the library cannot be used in non-React apps, which in fact, I didn't notice at first. Normally you'd expect the library to have some helper classes that can be used together in a React context or whatever else store you prefer and have snippets for it in the docs. Righttt, the *docs*...

![MultiversX docs](/docs.png) -->

That's why I'm writing this blog - to help myself and others finally escape the circlejerk of what framework to use, and to make profound choices instead of jumping on the hype train.

So, uhh, let my just start this by...

## Explaining how every single goddamn framework out there works

Ok, not really. But there's a way to distinguish and group them, a peculiarity that gets so overlooked that over my career of 4 years I missed it, although I've seen it multiple times and it's caused me issues before. I'm talking about **hydration**.

The first time you learn about hydration is when it pops up in the console as an error, and if you're using Next.js like me, you've probably seen it, too. This error doesn't really affect anything. Funny enough, it can disappear after a while if you continue ignoring it, but most of time the console gives you a tip - you can't use \<button> inside of a  \<button>. Why does it cause such a big issue for buttons? and what the f*ck is hydration?

It would make sense if I talked about how the button even appears in your website, first. So here comes...

### Rendering

Rendering typically is the very first step that occurs when opening a website. A JS framework doesn't consist of plain HTML, it consists of instructions written in JS about where to put the HTML. Rendering takes those instructions and constructs your website like lego. This can happen either on the client-side(browser) or the server. There's a process that happens nevertheless - 

### Initial page display

Rendering is the process of taking HTML, CSS, and other web assets and transforming them into the visual representation of a web page that users see in their browsers. This involves processing the HTML and CSS to determine the layout and appearance of elements on the page.

In simple words, it's how
```html
<button onclick="console.log('Boom')">Boom</button>
```
gets transformed into <button onclick="console.log('Boom')">Boom</button>

### Client-Side Rendering (CSR)

Client side rendering can be explain as the process of taking 


### Hydration



If we use rendering and hydration as keys for  can be portrayed in a Sankey diagram because ChatGPT said it's a reasonable way to display it. Here are the trending frameworks sourced from [stateofjs.com](https://2022.stateofjs.com/en-US/libraries/front-end-frameworks/) categorized by their rendering and hydration.

![Framework Map](/frameworkmap.png)

And here's the data of the last State of JS survey from 2022