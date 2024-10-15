# ready-made-components--code-only

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](./LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-green.svg)](https://github.com/ArifMiah07/ready-made-components--code-only)

A curated library of reusable UI components and code snippets, designed for ease of use and efficiency in your daily development workflow. This repository serves as a **comprehensive library** of essential components like buttons, forms, navigation bars, carousels, icons, and more. The goal is to reduce repetitive work and provide high-quality, ready-to-use code components for any project.

---

## 📋 Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
  - [Button](#button)
  - [Dropdown](#dropdown)
  - [Form](#form)
    - [Register_Form](#register_form)
  - [Navbar](#navbar)
  - [Dropdown](#dropdown)
  - [Swiper](#swiper)
    - [Nested_Swiper](#nested_swiper)
  - [Icons](#icons)
  - [More Components](#more-components)
- [Customization](#customization)
- [Contributing](#contributing)
- [License](#license)

---

## 💡 Introduction

This repository provides a collection of **ready-made code components** commonly used across various web and mobile development projects. Each component is written with flexibility in mind, allowing you to integrate them quickly into your codebase with minimal customization. Whether you're building a small project or working on a large-scale application, these components can help **accelerate development** and maintain a consistent, professional look.

---

## 🚀 Features

- **Reusable**: Components can be easily reused across multiple projects.
- **Modular**: Code is organized in a modular way, making it easy to import just what you need.
- **Customizable**: Every component is designed with customization in mind, allowing for easy style and functionality adjustments.
- **Modern**: The components follow modern development practices and standards.
- **Scalable**: Suitable for both small and large-scale applications.
- **Comprehensive**: Includes UI elements like buttons, forms, navbars, dropdowns, and more.

---

## 🛠 Installation

Clone the repository to get started:

```bash
git clone https://github.com/ArifMiah07/ready-made-components--code-only.git
cd ready-made-components--code-only
```

---

## 📦 Usage
Each component comes with its own folder containing the necessary code and documentation. Here are some examples of how to use the components from this library:

## 🔘 Button
A simple, customizable button component.

```html
<button class="btn-primary">Click Me</button>
```
You can customize the class to fit your design preferences.

## Dropdown
A very simple custom dropdown component with react js

```jsx
import { useState } from 'react';
import { NavLink } from 'react-router-dom';

const CustomDropdown = () => {
  const [isOpen, setIsOpen] = useState(false);

  const toggleDropdown = () => setIsOpen(!isOpen);

  return (
    <li className="relative">
      <button
        onClick={toggleDropdown}
        className="bg-transparent text-[16px] px-3 py-2 work-sans font-medium text-black hover:text-white focus:text-white focus:outline-none"
      >
        All Tourists Spot
      </button>
      {isOpen && (
        <ul className="absolute bg-white border rounded shadow-lg mt-2">
          <li>
            <NavLink
              to="/asia"
              className="block px-4 py-2 text-gray-700 hover:bg-gray-100"
              onClick={() => setIsOpen(false)}
            >
              Asia
            </NavLink>
          </li>
          <li>
            <NavLink
              to="/africa"
              className="block px-4 py-2 text-gray-700 hover:bg-gray-100"
              onClick={() => setIsOpen(false)}
            >
              Africa
            </NavLink>
          </li>
          <li>
            <NavLink
              to="/australia"
              className="block px-4 py-2 text-gray-700 hover:bg-gray-100"
              onClick={() => setIsOpen(false)}
            >
              Australia
            </NavLink>
          </li>
          <li>
            <NavLink
              to="/antarctica"
              className="block px-4 py-2 text-gray-700 hover:bg-gray-100"
              onClick={() => setIsOpen(false)}
            >
              Antarctica
            </NavLink>
          </li>
          <li>
            <NavLink
              to="/europe"
              className="block px-4 py-2 text-gray-700 hover:bg-gray-100"
              onClick={() => setIsOpen(false)}
            >
              Europe
            </NavLink>
          </li>
          <li>
            <NavLink
              to="/north-america"
              className="block px-4 py-2 text-gray-700 hover:bg-gray-100"
              onClick={() => setIsOpen(false)}
            >
              North America
            </NavLink>
          </li>
          <li>
            <NavLink
              to="/south-america"
              className="block px-4 py-2 text-gray-700 hover:bg-gray-100"
              onClick={() => setIsOpen(false)}
            >
              South America
            </NavLink>
          </li>
        </ul>
      )}
    </li>
  );
};

export default CustomDropdown;
```

## 📝 Form

--- 

A basic form template for handling user inputs.

```html
<form>
  <input type="text" name="username" placeholder="Enter your username" />
  <input type="password" name="password" placeholder="Enter your password" />
  <button type="submit">Submit</button>
</form>
```

### 🎉Register_Form

A basic form with context api and backend presence 

```jsx

import { Link, useLocation, useNavigate } from "react-router-dom";

import register from '../../assets/images/auth/register.jpg';

import { FaEye, FaEyeSlash, FaFacebook, FaLinkedin } from "react-icons/fa";

import { FcGoogle } from "react-icons/fc";

import { useContext, useId, useState } from "react";

import { AuthContext } from "../../Contexts/AuthProvider";

import NavBar from "../Shared/NavBar/NavBar";

  

import { ToastContainer, toast } from 'react-toastify';

import 'react-toastify/dist/ReactToastify.css';

  

const Register = () => {

  

    const [showPassword, setShowPassword] = useState(false);

    const { createUser, signInWithGoogle} = useContext(AuthContext);

    const location = useLocation();

    const navigate = useNavigate();

  
  

    const handleCreateUser = async (event) => {

        event.preventDefault();

        const form = event.target;

        const name = form.name.value;

        const email = form.email.value;

        const password = form.password.value;

        const userInfo = {

            name,

            email,

            password

        }

        // console.log(userInfo);

        createUser(email, password)

        .then(result => {

            const user = result.user;

            form.reset();

            navigate(location.state?.from || '/');

            toast.success('Registration Successful!')

            console.log(user)

        })

        .catch(error => toast.error(error))

    };

    const handleGoogleSignUp = async () => {

        try {

            await signInWithGoogle();

            toast.success("Login successful!");

            navigate(location.state?.from || '/');

        } catch (error) {

            toast.error(error.message);

            console.error(error);

        }

    };

    return (

        <div className="  ">

            <div>

                <NavBar></NavBar>

            </div>

            <ToastContainer />

            <div className="hero-content flex-col lg:flex-row">

                <div className="text-center lg:text-left lg:w-1/2">

                    <img src={register} alt="" />

                </div>

                <div className="card shrink-0 w-full lg:w-1/2 max-w-sm shadow-2xl bg-base-100">

                    <form onSubmit={handleCreateUser} className="bg-[#00DFC0] card-body">

                        <h1 className="text-3xl font-bold text-[#444444] text-center">Sign Up</h1>

                        <div className="form-control">

                            <label className="label">

                                <span className="label-text">Name</span>

                            </label>

                            <input name="name" type="text" placeholder="name" className="input input-bordered" required />

                        </div>

                        <div className="form-control">

                            <label className="label">

                                <span className="label-text">Email</span>

                            </label>

                            <input name="email" type="email" placeholder="email" className="input input-bordered" required />

                        </div>

                        <div className="form-control">

                            <label className="label">

                                <span className="label-text">Password</span>

                            </label>

                            <input name="password" type={showPassword ? "text" : "password"} placeholder="password" className="input input-bordered" required />

                            <span className="absolute inset-y-0 right-4 flex items-center cursor-pointer" onClick={() => setShowPassword(!showPassword)}>

                                {showPassword ? <FaEyeSlash /> : <FaEye />}

                            </span>

                        </div>

                        <div className="form-control mt-6">

                            <input className="btn btn-primary" type="submit" value="Sign Up" />

                        </div>

                        <div className="flex flex-col items-center gap-6">

                            <h1>Or Sign In with</h1>

                            <div className="flex gap-6">

                                <button type="button" className="btn btn-circle" onClick={handleGoogleSignUp}><FcGoogle /></button>

                                <button className="btn btn-circle"><FaFacebook /></button>

                                <button className="btn btn-circle"><FaLinkedin /></button>

                            </div>

                        </div>

                    </form>

                    <div className="mb-4">

                        <p className="text-center">Already have an account? <Link to="/login">Log In</Link></p>

                    </div>

                </div>

            </div>

        </div>

    );

};

  

export default Register;

```

--- 

## 🧭 Navbar
A responsive navigation bar structure.

```html
<nav class="navbar">
  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#">About</a></li>
    <li><a href="#">Services</a></li>
    <li><a href="#">Contact</a></li>
  </ul>
</nav>
```
## 📂 Dropdown
A simple dropdown menu.

```html
<div class="dropdown">
  <button class="dropdown-toggle">Dropdown</button>
  <div class="dropdown-menu">
    <a href="#">Option 1</a>
    <a href="#">Option 2</a>
  </div>
</div>
```
## 🎠 Swiper

--- 

A basic swiper/carousel component.

```html
<div class="swiper-container">
  <div class="swiper-wrapper">
    <div class="swiper-slide">Slide 1</div>
    <div class="swiper-slide">Slide 2</div>
    <div class="swiper-slide">Slide 3</div>
  </div>
  <!-- Add navigation controls -->
  <div class="swiper-button-next"></div>
  <div class="swiper-button-prev"></div>
</div>
```

### ✨ Nested_Swiper

```jsx
{/* main swiper */}
<Swiper
    className="mySwiper swiper-h h-full"
    spaceBetween={50}
    pagination={{
        clickable: true,
    }}
    modules={[Pagination]}
>
    {/* main swiperSlide */}
    {/* swiper slide 1 */}
    <SwiperSlide>
        <div className="h-full"> {/* i got some bug here; So, Ensure full height for the vertical swiper */}
            {/* Sub swiperSlide */}
            <Swiper
                className="mySwiper2 swiper-v h-full"
                direction={'vertical'}
                spaceBetween={30}
                pagination={{
                    clickable: true,
                }}
                modules={[Pagination]}
            >
                <SwiperSlide>
                    <div className='relative group'>
                        {/* Hover text overlay */}
                        <div className="absolute inset-0 flex flex-col justify-center items-center z-50 p-4 transition-opacity duration-300 opacity-0 group-hover:opacity-100 bg-black bg-opacity-70">
                            <a href="https://ideogram.ai/assets/image/lossless/response/eq_Iig4uS-Gw_Fq_tIXpBA" target='_blank' rel="noopener noreferrer" className='w-full h-full flex flex-col justify-center'>
                                <div className='flex flex-col justify-between opacity-80 w-full h-full'>
                                    <p className="p-4 mb-8 font-montserrat bg-gradient-to-r from-indigo-500 via-sky-500 to-emerald-500 w-full text-center">
                                        <TypeAnimation
                                            sequence={[
                                                'draw: minimalistic image of penguin, dark, 8k, illustration',
                                                1000,
                                                'A striking minimalistic illustration of a solitary penguin in the dark. The penguin is rendered in a monochrome palette with a touch of blue to emphasize its unique features. The background is a deep, dark abyss that adds to the mysterious atmosphere. The overall composition is both elegant and dramatic, with sharp lines and contrasts that make the penguin stand out in the high-resolution image.',
                                                1000,
                                            ]}
                                            wrapper='p'
                                            speed={50}
                                            className='text-xs sm:text-sm md:text-base lg:text-lg xl:text-xl'
                                            repeat={0}
                                        />
                                    </p>
                                </div>
                            </a>
                        </div>

                        {/* Image Container */}
                        <div className="relative w-full h-full">
                            <a href="https://ideogram.ai/assets/image/lossless/response/eq_Iig4uS-Gw_Fq_tIXpBA" target='_blank' rel="noopener noreferrer">
                                <img
                                    src="https://ideogram.ai/assets/image/lossless/response/eq_Iig4uS-Gw_Fq_tIXpBA"
                                    alt="Penguin Illustration"
                                    className="object-cover w-full h-full transition-transform duration-500 transform group-hover:scale-105"
                                />
                            </a>
                        </div>
                    </div>
                </SwiperSlide>

                <SwiperSlide>
                    <a href="https://ideogram.ai/assets/image/lossless/response/82zEfkJDTCG8yJzMa8ICnA" target='_blank'>
                        <img src="https://ideogram.ai/assets/image/lossless/response/82zEfkJDTCG8yJzMa8ICnA" alt="" />
                    </a>
                </SwiperSlide>
                <SwiperSlide>
                    <a href="https://ideogram.ai/assets/image/lossless/response/ex9dMrDHQ9ua4pWy-brPnQ" target='_blank'>
                        <img src="https://ideogram.ai/assets/image/lossless/response/ex9dMrDHQ9ua4pWy-brPnQ" alt="" />
                    </a>
                </SwiperSlide>
                <SwiperSlide>
                    <a href="https://ideogram.ai/assets/image/lossless/response/t6LEDHTmQMO0gdu-TA0OfA" target='_blank'>
                        <img src="https://ideogram.ai/assets/image/lossless/response/t6LEDHTmQMO0gdu-TA0OfA" alt="" />
                    </a>
                </SwiperSlide>
            </Swiper>
        </div>
    </SwiperSlide>
    {/* swiper slide 2 */}
    <SwiperSlide>
        <div className="h-full"> {/* i got some bug here; So, Ensure full height for the vertical swiper */}
            {/* Sub swiperSlide */}
            <Swiper
                className="mySwiper2 swiper-v h-full"
                direction={'vertical'}
                spaceBetween={30}
                pagination={{
                    clickable: true,
                }}
                modules={[Pagination]}
            >
                {/* SUb swiperSlide */}
                <SwiperSlide>
                    <div className="relative group">
                        {/* Hover text overlay */}
                        <div className="absolute inset-0 flex flex-col justify-center items-center z-50 p-4 transition-opacity duration-300 opacity-0 group-hover:opacity-100 bg-black bg-opacity-70">
                            <a href="https://ideogram.ai/api/images/direct/6aED-eIPSNCEVWjKtELLQA.jpg" target="_blank" rel="noopener noreferrer" className="w-full h-full">
                                <div className="relative flex flex-col items-center justify-center opacity-80 w-full h-full">
                                    <p className="absolute top-0 left-0 p-4 font-montserrat bg-gradient-to-r from-indigo-500 via-sky-500 to-emerald-500 w-full text-center">
                                        <TypeAnimation
                                            sequence={[
                                                'Design an informative, visually striking logo for a Facebook group titled "Batman AI Art." The logo should prominently display the group\'s name, "Batman AI Art," as the main subject. In the left corner, include text that reads: "A Facebook group with over 100K members," ensuring it complements the overall design. Incorporate elements that reflect both the Batman theme and the creative essence of AI art.',
                                                1000,
                                                'A visually striking logo for the Facebook group "Batman AI Art". In the center, there is a silhouette of Batman with the background as a city skyline. The Batman silhouette is created through the use of AI art. Below the silhouette, the text "Batman AI Art" is written in bold, black font. In the left corner, there is a subtle text that reads "A Facebook group with over 100K members". The overall design has a dark background.',
                                                1000,
                                            ]}
                                            wrapper="p"
                                            speed={50}
                                            className="text-xs sm:text-sm md:text-base lg:text-lg xl:text-xl"
                                            repeat={0}
                                        />
                                    </p>
                                </div>
                            </a>
                        </div>

                        {/* Image Container */}
                        <div className="relative w-full h-full">
                            <a href="https://ideogram.ai/api/images/direct/6aED-eIPSNCEVWjKtELLQA.jpg" target="_blank" rel="noopener noreferrer">
                                <img
                                    src="https://ideogram.ai/api/images/direct/6aED-eIPSNCEVWjKtELLQA.jpg"
                                    alt="Batman AI Art"
                                    className="object-cover w-full h-full transition-transform duration-500 transform group-hover:scale-105"
                                />
                            </a>
                        </div>
                    </div>
                </SwiperSlide>

                <SwiperSlide>
                    <div className="div-con">
                        <div className="imgg">
                            <a href="https://ideogram.ai/api/images/direct/6aED-eIPSNCEVWjKtELLQA.jpg" target="_blank">
                                <img src="https://ideogram.ai/api/images/direct/6aED-eIPSNCEVWjKtELLQA.jpg" alt="Focused Image" />
                            </a>
                        </div>
                    </div>
                    {/* <a href="https://ideogram.ai/api/images/direct/IkvsN6dyRXCNKheFBU5Ygg.jpg" target='_blank'>
                        <img src="https://ideogram.ai/api/images/direct/IkvsN6dyRXCNKheFBU5Ygg.jpg" alt="" />
                    </a> */}
                </SwiperSlide>
                <SwiperSlide>
                    <div className="div-con">
                        <div className="imgg">
                            <a href="https://ideogram.ai/api/images/direct/6aED-eIPSNCEVWjKtELLQA.jpg" target="_blank">
                                <img src="https://ideogram.ai/api/images/direct/6aED-eIPSNCEVWjKtELLQA.jpg" alt="Focused Image" />
                            </a>
                        </div>
                    </div>
                    {/* <a href="https://ideogram.ai/api/images/direct/UsiTrikTQhy63Qr4m4pnFw.jpg" target='_blank'>
                        <img src="https://ideogram.ai/api/images/direct/UsiTrikTQhy63Qr4m4pnFw.jpg" alt="" />
                    </a> */}
                </SwiperSlide>
                <SwiperSlide>
                    <div className="div-con">
                        <div className="imgg">
                            <a href="https://ideogram.ai/api/images/direct/6aED-eIPSNCEVWjKtELLQA.jpg" target="_blank">
                                <img src="https://ideogram.ai/api/images/direct/6aED-eIPSNCEVWjKtELLQA.jpg" alt="Focused Image" />
                            </a>
                        </div>
                    </div>
                    {/* <a href="https://ideogram.ai/api/images/direct/afYh2zK0Q1y7OKvmzeo5gg.jpg" target='_blank'>
                        <img className='' src="https://ideogram.ai/api/images/direct/afYh2zK0Q1y7OKvmzeo5gg.jpg" alt="" />
                    </a> */}
                </SwiperSlide>
                <SwiperSlide>
                    <div className="div-con">
                        <div className="imgg">
                            <a href="https://ideogram.ai/api/images/direct/6aED-eIPSNCEVWjKtELLQA.jpg" target="_blank">
                                <img src="https://ideogram.ai/api/images/direct/6aED-eIPSNCEVWjKtELLQA.jpg" alt="Focused Image" />
                            </a>
                        </div>
                    </div>
                    {/* <a href="https://ideogram.ai/api/images/direct/afYh2zK0Q1y7OKvmzeo5gg.jpg" target='_blank'>
                        <img className='' src="https://ideogram.ai/api/images/direct/afYh2zK0Q1y7OKvmzeo5gg.jpg" alt="" />
                    </a> */}
                </SwiperSlide>
            </Swiper>
        </div>
    </SwiperSlide>
</Swiper>

```


## 🖼 Icons
Example of embedding an icon component.

```html
<i class="icon icon-home"></i> <!-- Customizable icon class -->
```
## ⌛ More Components
This repository includes many more components such as modals, accordions, progress bars, and more. Browse the components directory for a full list.

## 🎨 Customization
All components are fully customizable. You can adjust the CSS, HTML, and JavaScript as needed to fit your project's design and functionality.

For example, to customize the button colors, simply update the .btn-primary class in your CSS file:

```css
.btn-primary {
  background-color: #3498db;
  color: #fff;
  border-radius: 4px;
}
```
Feel free to adjust animations, layout, and structure as per your requirements.

---

## 🤝 Contributing
Contributions are welcome! Please follow these steps to contribute:

Fork this repository.
Create your feature branch: git checkout -b feature/my-feature.
Commit your changes: git commit -m 'Add feature'.
Push to the branch: git push origin feature/my-feature.
Open a pull request.
We appreciate contributions that enhance existing components, add new components, or improve documentation.

--- 

## 📄 License
This project is licensed under the MIT License. See the LICENSE file for details.

--- 

## 💬 Support
For any questions, feel free to open an issue or reach out at [arifmiah.me101gmail.com](mailto:arifmiah.me101gmail.com).

--- 

This `README.md` provides a **detailed yet customizable structure**, allowing you to adapt or expand it as your repository grows. Each section is designed with **clarity and professionalism** in mind, suitable for sharing with a professional development community.
