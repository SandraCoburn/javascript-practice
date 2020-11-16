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
