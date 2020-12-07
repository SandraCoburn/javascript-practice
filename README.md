# javascript-practice

html, css and javascript only. 30 days of javascript tutorial.

##### Exercise 2 - Have a function that makes clock hands move by hours, minutes and seconds

```
    <script>
      const secondHand = document.querySelector('.second-hand');
      const minsHand = document.querySelector('.min-hand');
      const hourHand = document.querySelector('.hour-hand');
      function setDate() {
        const now = new Date();
        const seconds = now.getSeconds();
        const secondsDegrees = (seconds / 60) * 360 + 90;
        secondHand.style.transform = `rotate(${secondsDegrees}deg)`;

        const mins = now.getMinutes();
        const minDegrees = (mins / 60) * 360 + 90;
        minsHand.style.transform = `rotate(${minDegrees}deg)`;

        const hours = now.getHours();
        const hoursDegrees = (hour / 12) * 360 + 90;
        hourHand.style.transform = `rotate(${hoursDegrees}deg)`;
      }
      setInterval(setDate, 1000);
    </script>
```

##### Exercise 3 - CSS Variables. Have a function that updates css variables to change spacing, blur and base color in a picture

```
  <script>
      const inputs = document.querySelectorAll('.controls input');
      function handleUpdate() {
        const suffix = this.dataset.sizing || '';
        document.documentElement.style.setProperty(
          `--${this.name}`,
          this.value + suffix
        );
      }
      inputs.forEach((input) => input.addEventListener('change', handleUpdate));
      inputs.forEach((input) =>
        input.addEventListener('mousemove', handleUpdate)
      );
    </script>
```

##### Exercise 4 - Array Cardio Day 1. Practice with Arrays methods. Learned that console.table will console a nice table with data on the console.

```
  const inventorsFiltered = inventors.filter((inventor) => {
        return inventor.year >= 1500 && inventor.year < 1600;
      });
      console.table(inventorsFiltered);
```

Also, to reduce an array of items that are repeated you use an object in the reducer. It will return: {car:5,bike:2,walk:2,van:2} ex:

```
const data: ['car',
        'car',
        'truck',
        'truck',
        'bike',
        'walk',
        'car',
        'van',
        'bike',
        'walk',
        'car',
        'van',
        'car',
        'truck',]
const sumInst = data.reduce((obj, d) => {
        if (!obj[d]) {
          obj[d] = 0;
        }
        obj[d]++;
        return obj;
      }, {});
```

##### Exercise 5 Flex Panel Image Gallery

Use of nested flexbox to have 5 panel behave in a way that we don't need to provide width. Only flexbox. With some javascript those panel will show only certain text and the javascript will modify the width of a selected panel:

```
   .panel {
        flex: 1;
        justify-content: center;
        align-items: center;
        display: flex;
        flex-direction: column;
        background: #6b0f9c;
        box-shadow: inset 0 0 0 5px rgba(255, 255, 255, 0.1);
        color: white;
        text-align: center;
        align-items: center;
        /* Safari transitionend event.propertyName === flex */
        /* Chrome + FF transitionend event.propertyName === flex-grow */
        transition: font-size 0.7s cubic-bezier(0.61, -0.19, 0.7, -0.11),
          flex 0.7s cubic-bezier(0.61, -0.19, 0.7, -0.11), background 0.2s;
        font-size: 20px;
        background-size: cover;
        background-position: center;
      }
 .panel.open {
        font-size: 40px;
        flex: 5;
      }

 <script>
      const panels = document.querySelectorAll('.panel');
      function toggleOpen() {
        this.classList.toggle('open');
      }
      function toggleActive(e) {
        if (e.propertyName.includes('flex')) {
          this.classList.toggle('open-active');
        }
      }
      panels.forEach((panel) => panel.addEventListener('click', toggleOpen));
      panels.forEach((panel) =>
        panel.addEventListener('transitionend', toggleActive)
      );
    </script>
```

##### 06 Ajax type ahead

Get data from an API and add it to an array so it can be searched and displayed:

```
  const endpoint =
        'https://gist.githubusercontent.com/Miserlou/c5cd8364bf9b2420bb29/raw/2bf258763cdddd704f8ffd3ea9a3e81d25e2c6f6/cities.json';
      const cities = [];

      fetch(endpoint)
        .then((data) => data.json())
        .then((data) => cities.push(...data));
```

##### 07 Array Cardio Dary 2

Use of Array prototype methods: some(), every(), find(), findIndex()

```
const isAdult = people.some((person) => new Date().getFullYear() - person.year >= 19);
const allAdults = people.every((person) => new Date().getFullYear() - person.year >= 19);
const findComment = comments.find((comment) => comment.id === 823423);
const index = comments.findIndex((comment) => comment.id === 823423);
```
