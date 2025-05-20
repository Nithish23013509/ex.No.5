# Ex05 Image Carousel
## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
## ImageCarousel.jsx
```
import React, { useState } from "react";

const images = [
  "https://imgs.search.brave.com/TdAdCaJqoENJ6SmIFt3FqWveOwucR5xxaJHhSDCdi7g/rs:fit:500:0:0:0/g:ce/aHR0cHM6Ly9pbWFn/ZXMudGVtcGxhdGUu/bmV0L3dwLWNvbnRl/bnQvdXBsb2Fkcy8y/MDE2LzA0LzI3MDk0/MzM0L0VsZWdhbnQt/Q2FyLVdhbGxwYXBl/ci1mb3ItRG93bmxv/YWQuanBn",
  "https://imgs.search.brave.com/67mNyIo4BNDqpE1Yo18t32Fvx70t9Zi1kWIfddq37tE/rs:fit:500:0:0:0/g:ce/aHR0cHM6Ly9pbWFn/ZXMudGVtcGxhdGUu/bmV0L3dwLWNvbnRl/bnQvdXBsb2Fkcy8y/MDE2LzA0LzI3MTAw/NDUzL0Nvb2wtQ2Fy/LVdhbGxwYXBlci1m/b3ItRG93bmxvYWQu/anBn",
  "https://imgs.search.brave.com/FeOp8QNDS3XxZVT6ZmwVRx1sYbU_lfayuSH9WsLbyb8/rs:fit:500:0:0:0/g:ce/aHR0cHM6Ly9pbWFn/ZXMudGVtcGxhdGUu/bmV0L3dwLWNvbnRl/bnQvdXBsb2Fkcy8y/MDE2LzA0LzI3MDkz/MjE5L1B1cmUtQmxh/Y2stQ2FyLVdhbGxw/YXBlci5qcGc"
];

const ImageCarousel = () => {
  const [current, setCurrent] = useState(0);

  const nextSlide = () => {
    setCurrent((prev) => (prev + 1) % images.length);
  };

  const prevSlide = () => {
    setCurrent((prev) => (prev - 1 + images.length) % images.length);
  };

  return (
    <div style={styles.container}>
      <button onClick={prevSlide} style={styles.button}>❮</button>
      <img src={images[current]} alt={`Slide ${current}`} style={styles.image} />
      <button onClick={nextSlide} style={styles.button}>❯</button>
    </div>
  );
};

const styles = {
  container: {
    display: "flex",
    alignItems: "center",
    justifyContent: "center",
    gap: "10px",
    marginTop: "20px"
  },
  image: {
    width: "400px",
    height: "200px",
    borderRadius: "10px",
    objectFit: "cover",
    boxShadow: "0 4px 10px rgba(0,0,0,0.2)"
  },
  button: {
    fontSize: "24px",
    cursor: "pointer",
    background: "none",
    border: "none"
  }
};

export default ImageCarousel;
```
## index.css
```
:root {
  font-family: system-ui, Avenir, Helvetica, Arial, sans-serif;
  line-height: 1.5;
  font-weight: 400;

  color-scheme: light dark;
  color: rgba(255, 255, 255, 0.87);
  background-color: #242424;

  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

a {
  font-weight: 500;
  color: #646cff;
  text-decoration: inherit;
}
a:hover {
  color: #535bf2;
}

body {
  margin: 0;
  display: flex;
  place-items: center;
  min-width: 320px;
  min-height: 100vh;
}

h1 {
  text-align: center;
  font-size: 3.2em;
  line-height: 1.1;
}
h2 {
  text-align: center;
  font-size: 1.2em;
  line-height: 1.1;
  font-style: italic;
}

button {
  border-radius: 8px;
  border: 1px solid transparent;
  padding: 0.6em 1.2em;
  font-size: 1em;
  font-weight: 500;
  font-family: inherit;
  background-color: #1a1a1a;
  cursor: pointer;
  transition: border-color 0.25s;
}
button:hover {
  border-color: #646cff;
}
button:focus,
button:focus-visible {
  outline: 4px auto -webkit-focus-ring-color;
}

@media (prefers-color-scheme: light) {
  :root {
    color: #213547;
    background-color: #ffffff;
  }
  a:hover {
    color: #747bff;
  }
  button {
    background-color: #f9f9f9;
  }
}
.card{
    background-color: rgb(16, 116, 216);
    max-width: 200px;
    border: solid rgb(18, 214, 4) 8px;
    border-radius: 5px;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    margin: 10px;
    padding: 2px;
    text-align: center;
    display: inline-block;
  }
  .card img{
    width: 200px;
    height: 150px;
  }
:root {
  font-family: system-ui, Avenir, Helvetica, Arial, sans-serif;
  line-height: 1.5;
  font-weight: 400;

  color-scheme: light dark;
  color: rgba(255, 255, 255, 0.87);
  background: linear-gradient(-45deg, #ff9a9e, #fad0c4, #fad0c4, #fbc2eb, #a18cd1);
  background-size: 400% 400%;
  animation: gradientBG 15s ease infinite;

  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

@keyframes gradientBG {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
```

## OUTPUT
![Screenshot 2025-05-20 102656](https://github.com/user-attachments/assets/13487571-5026-4ceb-8780-c8c723a706cd)
![Screenshot 2025-05-20 102707](https://github.com/user-attachments/assets/aa1d8c58-b994-444d-85f9-643f807d7962)



## RESULT
The program for creating Image Carousel using React is executed successfully.
