#  React Tutorial and Projects Course (2022)

The repository contains the projects I created during the course [React Tutorial and Projects Course (2022)](https://www.udemy.com/course/react-tutorial-and-projects-course/learn/lecture/22580994#content).

## Description of the projects

- ### Birthday Reminder

A simple website that displays who is having a birthday today.

A [live version](https://petitoff-birthday-reminder.netlify.app/) of the page is available.

![clipboard.png](imgs/eGpp044og-clipboard.png)

The page gets data from the data.js file. The data is saved as an object in the list.

``` js
export default [
  {
    id: 1,
    name: 'Bertie Yates',
    age: 29,
    image: 'https://res.cloudinary.com/diqqf3eq2/image/upload/v1595959131/person-2_ipcjws.jpg',
  },
];
```
- ### Tours

Website with vacation spots for tourists. 

A [live version](https://petitoff-tours.netlify.app/) of the page is available.

![clipboard.png](imgs/l9jZrof3g-clipboard.png)

We are using api from `course-api.com`.
``` js
const url = "https://course-api.com/react-tours-project";
```

Fetching data from api as json format.
``` js
const fetchTours = async () => {
  setLoading(true);

  try {
    const response = await fetch(url);
    const tours = await response.json();
    setLoading(false);
    setTours(tours);
  } catch (error) {
    setLoading(false);
    console.log(error);
  }
};
```

Fetching the data takes place after the page has been loaded. Data is send via props to tour.jsx component.

- ### Reviews

Customer feedback slideshow.

A [live version](https://petitoff-reviews.netlify.app/) of the page is available

![clipboard.png](imgs/JmVS4rjBW-clipboard.png)

We are getting data from `data.js`
``` js
import people from "./data";
```

Restructuring from object and useState for changing the index of array in `Review.jsx`
``` js
const [index, setIndex] = useState(0);
const { name, job, image, text } = people[index];
```

Generate random index of the array `people`
``` js
let randomNumber = Math.floor(Math.random() * people.length);
```

Checking if we are not going out of the array
``` js
const checkNumber = (number) => {
  if (number > people.length - 1) {
    return 0;
  }

  if (number < 0) {
    return people.length - 1;
  }

  return number;
};
```