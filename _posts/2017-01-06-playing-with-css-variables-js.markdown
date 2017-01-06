---
layout: post
title: "3. Playing with CSS Variables and JS"
date: 2017-01-06T17:03:15-06:00
categories:
---

<div class="controls">
    <label for="spacing">Spacing:</label>
    <input id="spacing" type="range" name="spacing" min="10" max="200" value="10" data-sizing="px">

    <label for="blur">Blur:</label>
    <input id="blur" type="range" name="blur" min="0" max="25" value="0" data-sizing="px">

    <label for="base">Base Color</label>
    <input id="base" type="color" name="base" value="#ffc600">
  </div>

  <img src="https://source.unsplash.com/800x500">

  <style>
    :root {
    	--base: #FFC600;
    	--spacing: 10px;
    	--blur: 0px;
    }
	
		.h1 {
			color: var(--base);
		}

    /* Misc */

    img {
    	padding: var(--spacing);
    	background: var(--base);
    	filter: blur(var(--blur));
    }

    body {
      text-align: center;
    }
    body {
      background: #1c375b;
      color: white;
      font-family: 'helvetica neue', sans-serif;
      font-weight: 100;
      font-size: 50px;
    }
    .controls {
      margin-bottom: 50px;
    }
    input {
      width:100px;
    }
  </style>

  <script>
  	const inputs = document.querySelectorAll('.controls input');

  	function handleUpdate() {
  		const suffix = this.dataset.sizing || '';
  		document.documentElement.style.setProperty(`--${this.name}`, this.value + suffix);
  	}

  	inputs.forEach(input => input.addEventListener('change', handleUpdate));
  	inputs.forEach(input => input.addEventListener('mousemove', handleUpdate));

  </script>
