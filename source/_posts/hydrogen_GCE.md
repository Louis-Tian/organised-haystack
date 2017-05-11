---
title: Hydrogen + Google Compute Engine
subtitle: My setup for machine learning
date: 2017-05-01
categories:
- coding
tags:
- Machine learning
- Google Compute Engine
- Atom
- Hydrogen
---

Recently started became addicted to Kaggle.com.

### Why Google Compute Engine ?

Two reasons:
  1. Scalable
  2. Economical

Using GCE you can scale up and down as you wish, from a free single shared core micro instance up a 64-core beast machine with 416GB of RAM and 8 Tesla K80 GPU. If that's not enough, running a cluster of machines and sky is your limit.

This is not only more flexible but also heaps cheaper. Economy of scale, as an economist would say. And that's not even the best part. Most of the time you can even run with "Preemptible" instances which makes things even cheaper.

How does GCE compare against AWS, you ask? I don't know. But from what I hear, GCE is cheaper and has a way more intuitive UI.

### Why Hydrogen ?

Two reasons:
  1. Stay within the wonderful world of Atom.
  2. Finally, proper version control for your Jupiter notebooks.

Atom has a who bunch of goodies to offer, VIM key binding, Git integration.

We all love Jupiter but VC is hard for Jupiter notebooks. It's `html` with both inputs and outputs.
Try to a diff between two commit... Let's face it, it's crap. With Hydrogen, finally, you can have a
best of both world. Unlike Jupiter notebook, you write in a plain `.py` file.

#### STEP#1 - Start google compute engine

<pre><code class="shell">
$ gcloud start instance_name
</code></pre>

Not much is going on here. That's right.

This part is the excerpt, get it with the

<!-- more -->
