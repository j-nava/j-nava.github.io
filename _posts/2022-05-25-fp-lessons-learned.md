---
layout: post
title: "Imperative to functional programming: lessons learned"
---

Here I recount the pros and cons of developing a little animation software as a learning tool to abandon OOP in favor of functional programming. 

## The editor

![Example](/assets/images/2022-05-25-example.gif)

[^1]

The idea for this editor came from how unhappy I was with the standards for displaying simple vector animations on the web. 

GIFs are both big and bad quality (as can be easily observed on the GIF above...). Videos are clunky and sometimes hard to loop correctly and without a stutter. SVGs are great for still vector images, but animations (SMIL) aren't easy to work with if you're trying to do anything a little more complex. Same for CSS animations. 

Airbnb to the rescue! Yes, Airbnb and it's fantastic [Lottie](https://airbnb.io/lottie). 

But Lottie requires complicated, innaccessible software. If you're not _really_ an artist and want a simple solution, you're out of luck. 

This was my cue to get into functional programming once and for all. 

## The language

I had already played with Haskell before, but had never really _got_ it. After a while I've begun to grow afraid of Haskell. Not afraid of the language itself at the time (oh, the innocence!), but everything else. There were language extensions I didn't understand. Too many libraries that seemed to "do the same thing". The build system looked overcomplicated. 

Then I found out about **PureScript**. In the very beginning, it was especially appealling to me that if I missed anything in terms of library (or language knowledge!), I could use JavaScript instead with PureScript's straightforward foreign function interface (FFI). 

## The good

### Refactoring

As I made progress and felt the need to refactor my code, I started to notice how painless the process was. 10 times out of 10, after my code compiled again, it would just work. My (few and far between) tests would pass. 

Knowing that I could revisit my code later, change everything, and very rarely have a bug to fix gave me a lot of peace of mind! 

### Types

I was fortunate to read early on a blog post about one of the most important things I came to learn:

_Make illegal states unrepresentable._\
_Make illegal states unrepresentable._\
**Make illegal states unrepresentable.**

Another common philosophy (which I was not fortunate to learn in advance) that I ended up "inventing" myself was "_parse, not validate_". 

And that's all I have to say (for now...).

### Architecture

I like to joke about software architects that, especially in the OOP world, learn about a new design pattern and want to apply it to _everything_. It becomes a "let's find problems to solve with this" instead of "let's use this to solve that problem". 

After learning about mtl-style, I became that person. 

"Oh, so my program has a canvas? Easy. That's `MonadCanvas`. There's the editor itself! `MonadEditor`. Animation elements? `MonadAnimator` will deal with that!". And so on and so forth.

It was a time of writing typeclass instances. I admit that I learned a lot with it, and I'm also not saying that _none_ of it makes sense (I kept `MonadCanvas`!), but that's how I learned funcional programming is not immune to overengineering! 

But it the end, it was a positive experience. Again, strong types saving the day when I needed to refactor!

### Community

The PureScript community is not something to take for granted. I argue that it is one of biggest reasons I'm sticking with PureScript. 

They more than make up for that lack of information you'll find online. 

### Renewed passion

This is the first time since school that I'm not unfamiliar with type theory notation and some notions of lambda calculus. Studying category theory and having very expressive languages to directly experiment with is extremely satisfying. 

I will need at least three lifetimes to catch up with the community, but I don't see it as a bad thing! After all, if I learn something today and want to apply it to my existing codebase, refactoring is _that_ painless.  

## The bad

### Learning curve

It's easy to look back now and think that the barrier to entry to the functional programming world is not that high. 

But it took me a lot of patience with cryptic error messages (that make a lot of sense _now_, for the most part) and broken code to get over it and finally begin to be productive. 

### Information available

Being a somewhat niche programming paradigm, you won't find much information about what you need online. 

What is out there is usually high quality, but more and more I feel that the intermediate "steps" (between difference sources) are missing. Like the "[_How to draw an owl_](https://knowyourmeme.com/memes/how-to-draw-an-owl)" meme. 

## The future

Back to the editor, a new version is well under way. 

Hopefully, a similar blog post will come out of it in a future where I clearly see its shortcomings! 

---

[^1]: Source animation [here](https://lottiefiles.com/11282-bread-toaster). 

