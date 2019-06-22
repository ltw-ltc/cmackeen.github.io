---
layout: default
title: Edge Bleed Background
parent: Projects
---
<button class="btn js-toggle-dark-mode">~Nightmode~</button>

<script>
const toggleDarkMode = document.querySelector('.js-toggle-dark-mode')
const cssFile = document.querySelector('[rel="stylesheet"]')
const originalCssRef = cssFile.getAttribute('href')
const darkModeCssRef = originalCssRef.replace('just-the-docs.css', 'dark-mode-preview.css')

addEvent(toggleDarkMode, 'click', function(){
  if (cssFile.getAttribute('href') === originalCssRef) {
    cssFile.setAttribute('href', darkModeCssRef)
  } else {
    cssFile.setAttribute('href', originalCssRef)
  }
})
</script>


{% include lib/mathjax.html %}

# Simulated Pre-edge Subtraction 

{: .no_toc } When analyzing the fine structure
in the post edge of a spectrum, it is important to have rigorous background
removal. This is done generally with spline fitting of a slowly oscillating
background, where we can choose the number of knots using the Nyquist-Shannon sampling theorem:   $$ N_{\rm knots}  =  1 + \frac{2R_{\rm bkg} \Delta k}{\pi} $$ .

But there are occasions where another set of EXAFS oscillations of an edge around 300eV below your desired edge contribute to the background. Since this specific background is also EXAFS oscillations, it will not necessarily be filtered out by the generic spline fitting. 


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
## Simple yet specialized background subtraction in the pre-edge and beyond
*6/11/2019*
{: .fw-300 }


![](/assets/predge_bleed_91.png)

(source:JB Boyce, FG Bridges, T Claeson, *Local-Structure of BaBi$_x$Pb$_{1-x}$O$_3$ Determined by X-ray Absorption Spectroscopy* (1991) [link](/assets/bridgeboyce91.pdf) )


the procedure done then was not designed for batch use, and we have many temperatures and files to run over, so it is worth setting a framework where python can optimize a "stencil" fit to the large oscillations in the pre-edge.
![](/assets/esfit_stenc.jpg)

