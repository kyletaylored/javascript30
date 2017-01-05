---
layout: post
title: "2. CSS + JS Clock"
date: 2017-01-04T11:20:17-06:00
categories:
---

<style type="text/css" media="screen">
	.clock-container {
		width: 100%;
		height: 600px;
		background-image: url("https://unsplash.it/1275/600");
		background-size: cover;
		position: relative;
	}	
	.clock {
		margin: 0 auto;
		height: 300px;
		width: 300px;
		background-color: #ccc;
		border: 10px solid #fff;
		border-radius: 100%;
		transform: translateY(50%);
		position: relative;
		box-sizing: border-box;
		box-shadow: 0px 0px 10px 2px rgba(0,0,0,0.5), inset 0px 0px 8px 0px rgba(0,0,0,0.5);
    padding: 15px;
	}
	.hand {
		width: 125px;
		height: 6px;
		background:#777;
		border-bottom-left-radius: 5px;
		border-top-left-radius: 5px;
		position: absolute;
		top: 50%;
		transform-origin: 100%;
		transform: rotate(360deg);
		transition: all 0.5s;
		transition-timing-function: cubic-bezier(0, 2.2, 0.58, 1);
	}
</style>

<div class="clock-container">
	<div class="clock">
		<div class="hand hour"></div>
		<div class="hand minute"></div>
		<div class="hand second"></div>
	</div>
</div>

<script>
	const secondHand = document.querySelector(".hand.second");
	const minuteHand = document.querySelector(".hand.minute");
	const hourHand = document.querySelector(".hand.hour");

	function setDate() {
		const date = new Date();

		const seconds = date.getSeconds();
		const minutes = date.getMinutes();
		const hours = date.getHours();

		const time = {
			"seconds": {"time": seconds, "hand": secondHand},
			"minutes": {"time": minutes, "hand": minuteHand},
			"hours":   {"time": hours, "hand": hourHand}
		};
		
		// Write loop to make more efficient.
		for (let key in time) {
			if (time.hasOwnProperty(key)) {

				let prop = time[key];
    		let degrees = ((prop.time / 60) * 360) + 90;
    		let transform = `rotate(${degrees}deg)`;
    		prop.hand.style.transform = transform;
    		
    		// Set duration to 0 if passing over the top.
    		let duration = (degrees == 90) ? "0s" : "0.5s";
    		prop.hand.style.transitionDuration = duration;
    		
  		}
		}
	}
	
	setInterval(setDate, 1000);
</script>
