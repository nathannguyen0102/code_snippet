# code_snippet

Javascript
1. smooth scroll-roll:

const btnScroolTo = document.querySelector('.btn--scroll-to');
const section1 = document.querySelector('#section--1');

btnScroolTo.addEventListener('click', () => {
  section1.scrollIntoView({ behavior: 'smooth' });
});
