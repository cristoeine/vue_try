<template>
	<div>
	  <h1>JavaScript Timeline</h1>
	  <Timeline :timelineItems="timelineArray" />
	</div>
  </template>
  
  <script setup>  
  const timelineArray = ref([
	{
	  year: "1995",
	  event: "JavaScript Introduced by Brendan Eich at Netscape",
	},
	{
	  year: "1997",
	  event: "ECMAScript created to Standardize JavaScript",
	},
	{
	  year: "1999",
	  event: "ECMAScript3: Introduction of RegEx, try-catch",
	},
	{
	  year: "2009",
	  event: "ECMAScript5: strict mode, Object methods",
	},
	{
	  year: "2015",
	  event: "ES6: introduced classes, Arrow functions, let/const variables",
	},
	{
	  year: "2016 Onwards",
	  event: "Introducing features like async/await, spread/rest operators etc.",
	},
  ])
  </script>
  
  <style scoped>
  body {
	font-family: 'Arial', sans-serif;
	background-color: #a04040;
	margin: 0;
	padding: 20px;
  }
  
  h1 {
	text-align: center;
	color: #333;
  }
  </style>