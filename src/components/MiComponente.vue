<template>
    <button @click="handleClick">{{ buttonText }}</button>
  </template>
  
  <script>
  export default {
    data() {
      return {
        buttonText: 'Oprime'
      };
    },
    methods: {
      handleClick() {
        alert('¡Por que tan obediente jajaja!');
      }
    }
  }
  </script>
  
  <style>
  button {
    background-color: #007bff;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  </style>
  