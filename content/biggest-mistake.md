+++
title = "The biggest mistake of my early career"
date = 2023-04-12

[taxonomies]
categories = ["Thoughts", "Guides"]
+++

Mistakes are good. They imply you're in an uncomfortable place. It was so painful I left the company. But the business keeps chasing me to this day.

<!-- more -->

---

You see, starting a career is always challenging. There's a point where you have to take a leap and start making money with the knowledge you've supposedly gained during the process(I assume) you have spent learning.

You try finding a suitable job... and get accepted! Congrats! Now what?

When you start working at a company, you must go through an internship. It's where you show your skills and slowly get accustomed to the work environment you'll be in for quite a while. The internship phase was ambiguous - I was "learning" while already working on enterprise software. And let me tell you one thing - it was a disaster.

You develop a certain degree of Stockholm syndrome when joining a new company, especially if it's your first time and you're a junior developer(guess what, it's me). Now there are big Chad programmer guys who take you by your hand and lead you through the frameworks and procedures they used to make the software and how they work. And you listen carefully. You fool. No, no, it was me; I was the fool...

That's what internships are all about - learning for the better. The worst part is that they could have provided me with excellent and proven tutorials already available on the internet. No. The company CEO was hosting YouTube streams where he taught his ways of software development to innocent students, just like me. The points made in those streams were so far off and contradicted everything I had learned about so far. But I felt like I was enlightened at that moment. I thought, wow, such a unique approach; this must be super efficient!

Haha, yeah...

### The disaster

It all starts from this. My rant.

```js
const { EventEmitter } = require("events");

const firstEmitter = new EventEmitter();

firstEmitter.emit("My first event");
```

Yes, that's the most primitive event emitter written in [Javascript](https://developer.mozilla.org/en-US/docs/Web/javascript) - the core of all problems.
Doesn't sound too crazy, but if you know a little about how state management works in [React](https://react.dev/) and if I told you that state change was _always_ triggered by events... yeah... the face of disgust.

There was no possibility of debugging the code because HTTP requests were being made every 5 seconds, which means... *clears throat*... asynchronous event-based state changes every single time. And it wasn't just one state that lived happily in one component. It was state triggered across all components. You never knew which one could handle the event first. On top of that, every single React component extended the Node.js `EventEmitter` class. And the event handler itself was a HUGE class that reached 4k lines of code in one file. Absolute disaster.

### The redemption

Soon enough I realized that the codebase was pure insanity. I proposed a different approach to the people in charge of the project management, and the conversation went something like this:

- "Have you ever heard of a tool called [React Query](https://tanstack.com/query/latest)? It's a great tool that helps you deal exactly with this problem, but even way better than the framework does it natively."
- "Thanks, I will definitely check it out! 👍"

(P.S. Nobody ever checked it out)

So I tried tackling the problem on my own, to show an example of a much cleaner implementation. Surely someone had to see the difference it makes.

I'm too lazy to write the example of before and after, so here's just the after:

```tsx
function Component() {
    const [text, setText] = useState("");

    const { data: products } = useQuery(["products"], async () => {
        const { data } = await axios.get("...");
        return data;
    });

    return (
        {products?.map(p => (
            <div>
                {p.name}
            </div>
        ))}
    );
}
```

This solves one of the main problems - there are no events getting emitted when asynchronous data is received and everything stays tied to the relevant component. On top of that `React Query` offers caching and other cool features, which usually are pain in the ass to to implement by hand and most likely have to be implemented in your React application. How to avoid it? Just use [Svelte](https://svelte.dev/) instead bro.

Long story short, I got all my code rewritten by the CEO. And after that, they also decided to keep me away from the essential projects as I caused too much trouble. I ended up working on a poorly written `WordPress` theme in `PHP` for the rest of my time in misery.

That's when I decided to leave this place for good as there was no space for growth, even though I had no better job prospects at the moment.

Till this day, I still have nightmares of events emitting uncontrollably, but had I only known those nightmares would soon come to reality...

### The aftermath

The problem is - I live in a small town, and every IT person here knows the CEO. Heck, he even appears all around Latvia. I keep seeing him in every single event I go to.

I started a student company this year, which involves machine learning concepts. I sought a mentor to guide me through creating such solution. There were no results until one day... *The guy* texted me, saying he saw this student company on a public spreadsheet working on an AI solution, and asked if I knew the people behind it. Me, excited from being noticed, I proudly let him know it is I, the man himself.

Two weeks later I find myself enrolled in a deep learning course of his and also him offering me a "partnership" with my student company, where he, in the end of the day, keeps the biggest cut.

I was crushed. There was no way this could've possibly happened, I thought I had gotten away. No matter which direction I turned, I fell right into his hands.

You know, I'm not quite the expert in deep learning, but as far as my concerns go, his way of teaching it wasn't the best either, so I got scared of big formulas and hid away. Never replied to his messages.

Now, wherever I go, I feel like he's going to appear again out of nowhere and I'll be unknowingly dragged back into the cursed reality.

### What can you learn?

I know I talked so much shit and blamed the poor man for literally doing his job, but all he had to do was listen. Hear out the opinions of other people before diving head-first into writing bloated code(I really hope he's not reading this).

I'd really have liked to hear his opinion on why my approach is bad, although I understand that the constant pressure from the IT industry constantly evolving can be unbeareable, and it makes you stick to the roots you know work. But that's what teams are for - distribute the pressure to work towards a better solution. But who am I to tell at this point.

It's the effort you make towards making a solid connection with people that matters. You could give everything, even pizza and burgers on the weekends(they were pretty good though), but if you don't spend a single dime of your time to show empathy or simple appreciation towards the other person, it will all fall apart.

And be careful not to be misled by others telling you you're doing something wrong. Ask them - why? Do your research, use your own experience, but also remember to listen.

And don't hold me accountable for if anything goes wrong, you shouldn't be listening to a stranger on the internet anyway.