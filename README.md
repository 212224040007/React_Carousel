# React_Carousel
# Name: Abhishek Kannan M
# Regno:212224040007
# Date: 21/3/26

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

App.jsx

```
import { useState, useEffect } from "react";
import "./App.css";
import sun from "./sun.jpeg";
import moon from "./moon.jpg";
import earth from "./earth.jpg";

function App() {
  const images = [
    { src: sun, alt: "Sun" },
    { src: moon, alt: "Moon" },
    { src: earth, alt: "Earth" },
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setCurrentIndex((prev) => (prev + 1) % images.length);
    }, 3000);
    return () => clearInterval(interval);
  }, []);

  return (
    <div className="carousel">
        <h1>   Solar Carousel 🌞🌙🌍</h1>
      <div className="image-container">
        <img
          src={images[currentIndex].src}
          alt={images[currentIndex].alt}
          className="fade"
        />
      </div>
      <div className="dots">
        {images.map((_, index) => (
          <span
            key={index}
            className={index === currentIndex ? "dot active" : "dot"}
            onClick={() => setCurrentIndex(index)}
          ></span>
        ))}
      </div>
    </div>
  );
}

export default App;

```

App.css

```
/* Center everything on the page */
.carousel {
  background-color: #001f3f;
  color: white;
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center; /* vertical center */
  align-items: center; /* horizontal center */
  text-align: center;
  overflow: hidden;
  margin: 0;
}

/* Title styling */
.carousel h1 {
  font-size: 2.5rem;
  margin-bottom: 20px;
  font-weight: bold;
}

/* Image box styling */
.image-container {
  width: 400px;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 0 30px rgba(255, 255, 255, 0.3);
}

/* Image fit and animation */
.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 20px;
  transition: opacity 1s ease-in-out;
}

/* Dot controls */
.dots {
  margin-top: 20px;
}

.dot {
  height: 12px;
  width: 12px;
  margin: 0 5px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  cursor: pointer;
  transition: background-color 0.3s;
}

.dot.active {
  background-color: white;
}

.fade {
  animation: fadeEffect 1s ease-in-out;
}

@keyframes fadeEffect {
  from {
    opacity: 0.5;
  }
  to {
    opacity: 1;
  }
}

/* Remove unwanted scroll bars or padding */
body, html {
  margin: 0;
  padding: 0;
  overflow: hidden;
}

```


## OUTPUT

<img width="1443" height="695" alt="Screenshot 2026-03-23 103036" src="https://github.com/user-attachments/assets/19085600-a109-45a3-8e13-f9e181f82471" />




<img width="1447" height="694" alt="Screenshot 2026-03-23 103105" src="https://github.com/user-attachments/assets/083892b5-47e1-48af-b54e-8b8d7ed38726" />

 
 
 
<img width="1433" height="692" alt="Screenshot 2026-03-23 103131" src="https://github.com/user-attachments/assets/5382a616-44df-4508-80b0-ff2f6d93d7c2" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
