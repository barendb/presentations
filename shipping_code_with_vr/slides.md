---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
---

# Shipping code with Vet Radar


<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: center
class: text-center
---

# What is Vet Radar doing, that allows us to iterate quickly and enabling us to ship to production multiple times a day?

---

# Easy, merge and walk away

Talk done

<v-click>

Vet Radar is tiny

We have few customers

All this will change when we get big... No it doesn't need too

</v-click>

---

# Let's unpack what makes this possible

And how this can get done at scale!

---

# Iterating quickly

- 🔎 **Feature scoping** - Scoping features for small deliverable blocks
- 🧑‍💻 **Developer practices** - making developers responsible
- 🧪 **QA practices** - devs and QA's working in sync
- 🛠 **Pipelines and tooling** - tools to allow engineers to ship with no effort
- 👀 **Observability** - have insight what your system is doing
- 👸 **Responsibility and accountability** - allowing everyone to ship to production
- ⛑ **Lots of safety nets** - do whatever we can to prevent disaster

---

# Feature scoping

Quick and dirty, work with your PO

- Break features down in the smallest deliverable blocks
- Determine what you're team can we deliver within a sprint?

**Talk to Brooke, he's been fundamental in helping to team come up with a small deliverable each sprint**

---

# Development

If you want to ship quickly you got to ship something small

<v-clicks>

- Code Blast radius 💥 smaller the change, easier to find bugs
- Large features, break them up in many small deliverables
- Use code level feature toggles (flags) to divert code that is not production ready
  - Code that is not used can't cause bugs? 🤔

</v-clicks>
---

# Feature toggles?

Feature toggles does not need to be a FANCY SYSTEM

```ts {all|2-7|8-11|14|all}
const FeatureToggles = {
  AWESOME_FEATURE: {
    developer: '@barend',
    created: '2021-08-01T05:35:45.842Z',
    enabled: true
  }
}

function isToggleEnabled(featureToggle: string) {
  return FeatureToggles[featureToggle].enabled;
}

function someFeatureInDevelopment() {
  if (!isToggleEnabled('AWESOME_FEATURE')) {
    console.log('current way of doing things');
    return;
  }
  
  console.log('the fancy new way of doing things');
}
```

---

# Development

If you want to ship quickly you got to ship something small

- Code Blast radius 💥 smaller the change, easier to find bugs (change delta 📐)
- Large features, break them up in many small deliverables
- Use code level feature toggles (flags) to divert code that is not production ready
  - Code that is not used can't cause bugs? 🤔

<v-clicks>
 
- Long-running features can be broken up into many many smaller pieces <br/>shipped to production and turned on when ready 
- Make it easy for your peers to review PR's
  - Small PR's are reviewed more thoroughly 
  - Tell a story with your PR, commit by commit
  
</v-clicks>
---

# QA Practices

Developers and QA need to work in Sync

Development is not a Ford factory, we don't throw stuff over the wall

<v-clicks>

- 🤯 QA's is not responsible for your code quality, they are (Quality Assistants)
- Use your QA to guide you around the minefield 💣
  - Talk about potential pitfalls before development starts
  - Determine what's needed to make what you're developing a success (test cases)
  - They are product specialists
- Proof to your QA what you've built works (tests)
- Use other engineers to help you test your code **before creating PR's** (Demo / Works On My Machine)

</v-clicks>

---

# Pipelines and tooling

You want to be able to deploy a code artifact quickly and be able to recover quickly

## Some considerations

<v-clicks>

- 🤖 **Automated** -- 100% automated deployments
- 🛠 **Deployment tools** - empower engineers to deploy code
- 👩‍🦽 **MTTR** - mean time to recover, how long does it take to fix a bad deployment?

</v-clicks>
---

# Observability

Developers operationally responsible for their deployments... yes DevOps

<v-clicks>

- **Observability tools/platforms** - Measure the internal state of your system
- **Monitor** - Gain insight how your deployment is fairing
- **Immediate feedback** - Immediately get feedback, is things fairing
- **Measure everything** - How do you know your code is working? Measure it? Metrics/Tracing

</v-clicks>

---

# Responsibility and accountability

You ship, you fix

- Engineers are responsible for fixing their own mistakes
- Engineers evaluate the risk and coordinate shipping risky artifacts

---

# Lots of safety nets

Confidence through safety

Believe that every engineer has the best intentions, if we (the team) *fuck* up, **it was an accident**.<br/>
One individual is not responsible, the code passed through many nets, and still slipped through?<br/>

<v-click>

- Tests
- Code Reviews
- WOMM
- QA

</v-click>

<v-click>

What allowed this accident to happen, what could we have done to prevent this accident.<br/>
Use blameless postmortems to determine the cause and implement safety nets to prevent it from happening again.<br/>
**Continuously improve process**

</v-click>

---

# Doing this at scale

This philosophy and practice is not new, it's borrowed, was lucky enough to learn form people way smarter than me

## Companies doing this at scale?

- Spotify
- Slack
- Netflix
- Etsy
- Pushpay (70+ engineers)

---
layout: end
class: text-center
---

# Learn More

[Documentations](https://sli.dev) · [GitHub](https://github.com/slidevjs/slidev) · [Showcases](https://sli.dev/showcases.html)
