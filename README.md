# ✡️ Learning React.js

🚀 React Learning Journey
This repository documents my React.js learning journey, starting from fundamentals and progressing toward building real-world, production-ready applications.

----

## 📌 Objective

- Build a strong foundation in React

- Understand modern React patterns and best practices

- Develop scalable, maintainable UI applications

- Prepare for internships, placements, and real-world projects

----
## 🧠 Learning Roadmap

### 1️⃣ React Fundamentals

- JSX & Rendering

- Components (Functional Components)

- Props & Default Props

- State Management (useState)

- Event Handling

- Conditional Rendering

-Lists & Keys

### 2️⃣ Core React Hooks

- useEffect

- useRef

- useContext

- Custom Hooks

### 3️⃣ Styling Approaches

- CSS & Flexbox

- CSS Modules

- Inline Styling

- Responsive Design Basics

### 4️⃣ Project-Based Learning

- To-Do Application

- Weather App (API Integration)

- Expense Tracker

- Mini Dashboard UI

- Portfolio Website

### 5️⃣ Advanced Concepts (Upcoming)

- React Router

- State Management (Context API)

- Performance Optimization

- Component Reusability

----

# 📈 Projects On Reacts

## 🪝Counter made by Hooks : 

```jsx
import React from 'react';
import { useState,useEffect } from 'react';
function List() {

    let [counter,setCounter]=useState(0);
    function incrementCounter(){
        setCounter(counter+1)
    }
    return(
        <>
            <h1>{counter}</h1>
            <h3>Counter Using useState Hook</h3>
            <button onClick={incrementCounter}>Click me</button>
        </>
    )
}

export default List;

```
----

## ✨ Background Color Changer :

```js
import React from "react";
import { useEffect,useState } from "react";
export default function Color(){

    let [color,SetColor]=useState("#cfcccc");

    function Changecolor(bgcolor){
        SetColor(bgcolor);
    }
    return(
        <>
        <body  style={{background:color}}>
            
        </body>
        <div className="container">
            <button onClick={()=>SetColor('blue')} id="blue">Blue</button>
            <button onClick={()=>SetColor('black')} id="black">Balck</button>
            <button onClick={()=>SetColor('red')} id="red">Red</button>
            <button onClick={()=>SetColor('#ad45f8')} id="violet">Violet</button>
            <button onClick={()=>SetColor('yellow')} id="yellow">Yellow</button>
            <button onClick={()=>SetColor('#4af70b')} id="green">green</button>
            <button onClick={()=>SetColor('cyan')} id="cyan">cyan</button>
            <button onClick={()=>SetColor('pink')} id="pink">pink</button>
        </div>
        </>
    )
}
```
---

## 🔑 Random Password Generator

```js
import React, { useState, useEffect, useCallback,useRef } from "react";

export default function Password() {
    const [passlen, setPasslen] = useState(8);
    const [numAllowed, setNumAllowed] = useState(false);
    const [charAllowed, setCharAllowed] = useState(false);
    const [specialAllowed, setSpecialAllowed] = useState(false);
    const [password, setPassword] = useState("");

    const Password_ref=useRef(null)
    const generatePassword = useCallback(() => {
        let pool = "";
        let result = "";

        const alphabets =
            "QWERTYUIOPASDFGHJKLZXCVBNMqwertyuiopasdfghjklzxcvbnm";
        const numbers = "1234567890";
        const specials = "!@#$%^&*(){}[]_/*+-?:;";

        if (numAllowed) pool += numbers;
        if (charAllowed) pool += alphabets;
        if (specialAllowed) pool += specials;

        if (!pool) return;

        for (let i = 0; i < passlen; i++) {
            const index = Math.floor(Math.random() * pool.length);
            result += pool[index];
        }

        setPassword(result);
    }, [passlen, numAllowed, charAllowed, specialAllowed]);

    const copyPassord=useCallback(()=>{
        window.navigator.clipboard.writeText(password);
    },[password])
    useEffect(() => {
        generatePassword();
    }, [generatePassword]);

    return (
        <>
            <h1>Password Generator</h1>

            <div className="input-box">
                <input type="text" value={password} readOnly ref={Password_ref} />
                <p onClick={copyPassord}>COPY</p>
                <button onClick={generatePassword}>Generate Password</button>
            </div>

            <div className="types">
                <div className="range">
                    <input
                        type="range"
                        min={6}
                        max={100}
                        value={passlen}
                        onChange={(e) => setPasslen(Number(e.target.value))}
                    />
                    <p>Length({passlen})</p>
                </div>

                <div className="items">
                    <div className="box">
                        <input
                        type="checkbox"
                        id="check1"
                        onChange={() => setNumAllowed((p) => !p)}
                    />
                    <label htmlFor="check1">Numbers</label>
                    </div>

                    <div className="box">
                        <input
                        type="checkbox"
                        id="check2"
                        onChange={() => setCharAllowed((p) => !p)}
                    />
                    <label htmlFor="check2">Characters</label>
                    </div>

                    <div className="box">
                        <input
                        type="checkbox"
                        id="check3"
                        onChange={() => setSpecialAllowed((p) => !p)}
                    />
                    <label htmlFor="check3">Special Characters</label>
                    </div>
                </div>
            </div>
        </>
    );
}

```
