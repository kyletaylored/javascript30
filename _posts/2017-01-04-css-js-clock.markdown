---
layout: post
title: "CSS + JS Clock"
date: 2017-01-04T11:20:17-06:00
categories:
---

<style type="text/css" media="screen">
	.clock-container {
		width: 100%;
		height: 600px;
		background-image: url("https://unsplash.it/1200/600");
		background-size: cover;
		position: relative;
	}	
	.clock {
		margin: 0 auto;
		height: 300px;
		width: 300px;
		background-color: transparent;
		border: 10px solid #FFF;
		border-radius: 100%;
		transform: translateY(50%);
		position: relative;
	}
	.hand {
		width: 45%;
		height: 6px;
		background:black;
		position: absolute;
		top: 50%;
		transform-origin: 100%;
		transform: rotate(360deg) translateX(5%);
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
	console.log(secondHand);

	function setDate() {
		const date = new Date();
		const seconds = date.getSeconds();
		const secondsDegrees = ((seconds / 60) * 360) + 90;

		const minutes = date.getMinutes();

		const hours = date.getHours();
		const time = [seconds, minutes, hours];
		console.table(time);
	}
	
	setInterval(setDate, 1000);
</script>
