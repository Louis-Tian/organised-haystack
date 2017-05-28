---
title: Hydrogen + Google Compute Engine
subtitle: My setup for machine learning
date: 2017-05-28
tags:
- Machine learning
- Google Compute Engine
- Atom
- Hydrogen
---
Recently, I became obsessed with Kaggle. I am still new to this whole ML business. And not long after a few `died kernels` or `Memory Error`, I knew my MacBook Pro is not really up for the tasks at hand. I started contemplating on building a new desktop system. My old one is already half a decade old. But hey it's 2017 having a desktop isn't the sexist idea. Then there comes Google offer $300 credit for trying their cloud platform. Google Compute Engine become an obvious choice.

Hardware isn't the only problem. In ML, `Python` is THE King. And when comes scientific computation `Jupyter` is the standard. However, keeping proper versioning in `Jupyter notebook` has always been a difficult task. Luckily, there is also solution to that as well. 'Atom' with `Hydrogen`.

This post is about how setup this powerful combo? And start ruling the Machine learning word.

<!--more-->

### Why Google Compute Engine (GCE)?

There are two main reasons:
1. Scalable
2. Economical

Using GCE you can scale up and down as you wish, from a free single shared core micro instance up a 64-core beast machine with 416GB of RAM and 8 Tesla K80 GPU. If that's not enough, running a cluster of machines and sky is your limit.

This is not only more flexible but also heaps cheaper. Economy of scale, as an economist would say. And that's not even the best part. Most of the time you can even run with "Preemptible" instances which makes things even cheaper.

I won't go into the details of how to get an Google Compute Engine instance up and running. The guys
at Google made it super easy, just go checkout the documentation [here](https://cloud.google.com/docs/)

I don't really use AWS, so I won't comment on the difference. But the most steps will be the same for both platforms, other than the parts involves `gcloud` commands.

The rest of the post will assume you have GCE setup and has the Google Cloud SDK installed.

### Why Hydrogen ?

`Hydrogen` is a `Atom` plugin. A very cool one. There are two main reasons of using it instead of vanilla `Jupyter` notebook in browser:
1. Stay within the wonderful world of Atom.
2. Finally, proper version control for your Jupiter notebooks.

Atom has a who bunch of goodies to offer, VIM key binding, Git integration.

We all love Jupiter but VC is hard for Jupiter notebooks. It's `html` with both inputs and outputs.
Try to a diff between two commit... Let's face it, it's crap. With Hydrogen, finally, you can have a
best of both world. Unlike Jupiter notebook, you write in a plain `.py` file.

### Set Thing UP

#### 1. Launch google cloud engine
<pre><code class="shell">
$ gcloud compute instance start instance_name --zone=your_instance_zoon
</code></pre>


#### 2. Turnoff Juptyer Token
Go to `~/.jupyter/.jupyter_notebook_config.py` and set `c.Notebookapp.token=''` to disable token. Since, we will be using SSH, we will still be secure without the token.


#### 3. Start Jupyter
<pre><code class="shell">
jupyter notebook --port=8888
</code></pre>


#### 4. Create SSH Tunnel
<pre><code class="shell">
ssh -N -L localhost:8888:localhost:8888 remote_username@remote_ip_address
</code></pre>
The external ip address will change every time you launch a new instance. You need get the remote_ip_address from step 1 every time. There must be a way to chain the two steps together, but I haven't explored to much on this.


#### 5. Config Hydrogen
Change the `Hydrogen`
<pre><code class="javascript">
[{
  "name": "Google Compute Engine",
  "options": { "baseUrl": "http://localhost:8888"}
}]
</code></pre>


#### 6. Connect Remote Kernel
* Go to your `.py` file.
* type `cmd-shift-p` to bring up the command palette.
* Search for`Hydrogen: Connect To Remote Kernel` and press enter.


#### 7.  Enjoy and Happy Coding.
