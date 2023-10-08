# code_snippet

Javascript snippet.

1. smooth scroll-roll:

//this is an example of event propagation.
//this is using event delagation.

document.querySelector('.nav-links').addEventListener('click', function (e) {
  e.preventDefault();

  // Matching strategy
  if (e.target.classList.contains('nav-link')) {
    const id = e.target.getAttribute('href');
    document.querySelector(id).scrollIntoView({ behavior: 'smooth' });
  }
});

//example of forEach loop (may not needed cz code above is delagation event)
nav.forEach(function (t) {
  t.addEventListener("click", function (e) {
    e.preventDefault();
    if (e.target.classList.contains("nav-link")) {
      const id = e.target.getAttribute("href");
      console.log(id);
      document.querySelector(id).scrollIntoView({ behavior: "smooth" });
    }
  });
});

2. Switch tab
3. 
//////////////
// Tabbed component

tabsContainer.addEventListener('click', function (e) {
  const clicked = e.target.closest('.operations__tab');

  // Guard clause
  if (!clicked) return;

  // Remove active classes
  tabs.forEach(t => t.classList.remove('operations__tab--active'));
  tabsContent.forEach(c => c.classList.remove('operations__content--active'));

  // Activate tab
  clicked.classList.add('operations__tab--active');

  // Activate content area
  document
    .querySelector(`.operations__content--${clicked.dataset.tab}`)
    .classList.add('operations__content--active');
});

3. Tab component
tabsContainer.addEventListener('click', function (e) {
  const clicked = e.target.closest('.operations__tab');

  // Guard clause
  if (!clicked) return;

  // Remove active classes
  tabs.forEach(t => t.classList.remove('operations__tab--active'));
  tabsContent.forEach(c => c.classList.remove('operations__content--active'));

  // Activate tab
  clicked.classList.add('operations__tab--active');

  // Activate content area
  document
    .querySelector(`.operations__content--${clicked.dataset.tab}`)
    .classList.add('operations__content--active');
});

4.// Sticky navigation: 
JS:
window.addEventListener("scroll", function () {
  const header = document.querySelector("header");
  header.classList.toggle("sticky", window.scrollY > 0);
});

CSS:
header {
  transition: all 0.6s ease;
  position: fixed;
  width: 100%;
  z-index: 99999999;
}
header.sticky {
  background: #1483d5;
  padding-bottom: 20px;
}


///////////////////////////////////////
5 Reveal sections
const allSections = document.querySelectorAll('.section');

const revealSection = function (entries, observer) {
  const [entry] = entries;

  if (!entry.isIntersecting) return;

  entry.target.classList.remove('section--hidden');
  observer.unobserve(entry.target);
};

const sectionObserver = new IntersectionObserver(revealSection, {
  root: null,
  threshold: 0.15,
});

allSections.forEach(function (section) {
  sectionObserver.observe(section);
  section.classList.add('section--hidden');
});

6 Lazy loading images
const imgTargets = document.querySelectorAll('img[data-src]');

const loadImg = function (entries, observer) {
  const [entry] = entries;

  if (!entry.isIntersecting) return;

  // Replace src with data-src
  entry.target.src = entry.target.dataset.src;

  entry.target.addEventListener('load', function () {
    entry.target.classList.remove('lazy-img');
  });

  observer.unobserve(entry.target);
};

const imgObserver = new IntersectionObserver(loadImg, {
  root: null,
  threshold: 0,

  7
  rootMargin: '200px',
});

imgTargets.forEach(img => imgObserver.observe(img));


**7. Fetch data from third party API:**

const input = document.querySelector(".input");
const btn = document.querySelector(".btn");
const img = document.querySelector(".img");
const display = document.querySelector(".display");

btn.addEventListener("click", function () {
  const value = input.value.trim();
  fetch(`https://www.themealdb.com/api/json/v1/1/filter.php?i=${value}`)
    .then((response) => response.json())
    .then((data) => {
      const arrayLength = data.meals.length;
      console.log(arrayLength);
      for (let i = 0; i < arrayLength; i++) {
        const img = document.createElement("img");
        display.appendChild(img);
        img.src = data.meals[i].strMealThumb;
        const foodName = document.createElement("p");
        display.appendChild(foodName);
        foodName.textContent = `${data.meals[i].strMeal}`;
      }
    });
});

**8. Align item inside a div grid**
.hero-div-right {
  justify-self: end;
}

**9. Align item inside a div grid**
10 react:

