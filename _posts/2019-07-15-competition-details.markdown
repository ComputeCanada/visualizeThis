---
layout: post
title:  "2019 competition details"
ref: welcome
date:   2019-07-15 09:48:44 +0100
categories: competition
lang: en
---

The theme of this year's challenge is **distributed rendering**, in other words, visualization of very
large datasets that require parallel rendering on a cluster. To participate in the challenge, please <a
href="https://www.eventbrite.ca/e/4th-annual-visualize-this-challenge-registration-71335547543"
target="_blank">register your interest</a>.

### Option 1: use your own data

We encourage you to use data from your own research, if you have a sufficiently large dataset. Any
dataset that is too large to be rendered on a standalone desktop/workstation will qualify for this
competition. A classic example is a time-dependent simulation in which disk space required to store each
timestep is comparable to or exceeds the workstation's RAM.

### Option 2: use the supplied (default) dataset

If you don't have access to such data, you can use the 3D computational fluid dynamics (CFD) dataset
kindly provided for this competition by Joshua Brinkerhoff (UBC Okanagan). This dataset comes from an
OpenFOAM numerical simulation of incompressible transitional air flow over a wind turbine section. The
fluid is treated incompressible due to the low Mach number. The airfoil is NACA0018, a common research
airfoil used to study wind turbine aerodynamics.

To reduce the size of the dataset, we include a fairly short time range ($$t=14.88308-15.01908$$) and
store five variables at every third timestep, resulting in 86 steps:

- *p* is the gauge static pressure (actually, static pressure divided by density, but density is constant
  in incompressible flow, so it functions as static pressure);
- *U* is the velocity vector;
- *vorticity* is the vorticity vector (curl of the velocity);
- *Lambda2* is the second eigenvalue of the symmetric tensor $$S^2+\Omega^2$$, where $$S$$ and $$\Omega$$
  are the symmetric and antisymmetric components of the velocity gradient tensor;
- *Q* is second invariant of the velocity gradient tensor.

Please note that while the first three variables (*p*, *U*, *vorticity*) are available for all 86
timesteps, the last two (*Lambda2*, *Q*) are available only for the fist 50 timesteps. Also note that
around $$t=14.92308$$, the timestep increases.

<!-- From the scientific perspective, -->
<!-- The underlying physical problem lies in understanding the separation of the laminar boundary layer from -->
<!-- the airfoil surface, the transition of the separated flow from a laminar state to turbulence, the -->
<!-- momentum exchange produced by the developing turbulence that allows the separated flow to reattach to the -->
<!-- blade surface. This process of separated flow transition is a critical process in the aerodynamics of -->
<!-- wind turbines, wings, gas turbines, etc. -->

Below, we provide a simple rendering of the velocity magnitude done with ParaView on the Cedar
cluster. The entire visualization with 286 frames took about 20 minutes to render on 64 CPU cores, with
most time spent on the time-dependent part towards the end of the video where we had to read each
timestep from disk.

<div class="flex-video">
	<iframe width="650" height="350" src="https://player.vimeo.com/video/353444320" frameborder="0"
	allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
	allowFullScreen mozallowfullscreen webkitAllowFullScreen></iframe>
</div>

<sup>(Or click <a href="https://vimeo.com/353444320" target="_blank">here</a> to watch this video
directly on Vimeo.)</sup>

Below is a more detailed look at the separation of the laminar boundary layer from the airfoil surface
and its transition to turbulence. This more complex rendering showing the isosurface of constant air
speed coloured by the Y-component of the vorticity took 17 minutes on 128 CPU cores on Cedar.

<div class="flex-video">
	<iframe width="650" height="350" src="https://player.vimeo.com/video/354038712" frameborder="0"
	allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
	allowFullScreen mozallowfullscreen webkitAllowFullScreen></iframe>
</div>

<sup>(Or click <a href="https://vimeo.com/354038712" target="_blank">here</a> to watch this video
directly on Vimeo.)</sup>

The default dataset will be available at the end of September on the Cedar, Graham, Niagara, and Béluga
clusters. You will need a <a
href="https://www.computecanada.ca/research-portal/account-management/apply-for-an-account"
target="_blank">Compute Canada account</a> (free to all Canadian researchers) to access the data. Since
the dataset is ~1.04 TB in size, we stronly advise *not* to copy or download it to your machine. Instead,
please read it directly into your visualization program from its original location.

Submissions are due by midnight Pacific Time (9 p.m. ET) on November 30, 2019.





<!-- You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated. -->

<!-- To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works. -->

<!-- Jekyll also offers powerful support for code snippets: -->

<!-- {% highlight ruby %} -->
<!-- def print_hi(name) -->
<!--   puts "Hi, #{name}" -->
<!-- end -->
<!-- print_hi('Tom') -->
<!-- #=> prints 'Hi, Tom' to STDOUT. -->
<!-- {% endhighlight %} -->

<!-- Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk]. -->

<!-- [jekyll-docs]: http://jekyllrb.com/docs/home -->
<!-- [jekyll-gh]:   https://github.com/jekyll/jekyll -->
<!-- [jekyll-talk]: https://talk.jekyllrb.com/ -->
