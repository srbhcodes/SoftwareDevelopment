---
tags:
  - topic
created: 2024-11-29
---
**Prerequisites**: [[01-React Topics]]

---

## **React's `useEffect` Explained in Depth**

### **1. `useEffect` Kya Hai?**
- `useEffect` ek React Hook hai jo **side effects** handle karne ke liye use hota hai.  
  Side effects ka matlab hai:
  - API calls (data fetch karna)
  - DOM manipulation
  - Timer/Interval set karna
  - Subscription/cleanup karna, etc.

---

### **2. `useEffect` Mein Kya Hota Hai?**
`useEffect` ke andar do main cheezein hoti hain:

1. **Callback Function:** Yeh woh code hai jo React ko run karna hai jab kuch dependency change ho.
   ```jsx
   useEffect(() => {
     console.log("Effect triggered!");
   });
   ```

2. **Dependency Array:** Is array ke andar woh variables ya functions hote hain jinpe React "depend" karega. Agar dependency array mein kuch change hoga, tabhi `useEffect` run karega.

   ```jsx
   useEffect(() => {
     console.log("Effect triggered!");
   }, [dependency1, dependency2]);
   ```

---

### **3. Dependency Array Kyu Hota Hai?**
- Dependency array React ko yeh batata hai:
  - **"Kab effect ko dubara chalana hai?"**
- React internally dependency array mein values ko compare karta hai (old vs new).
- Agar **dependency array na ho**, toh `useEffect` har render ke baad chalega. Example:

   ```jsx
   useEffect(() => {
     console.log("Effect triggered!");
   }); // No dependency -> Runs after every render
   ```

- Agar dependency array blank hai (`[]`), toh effect **sirf ek baar** chalega (component ke mount hone ke baad):
   ```jsx
   useEffect(() => {
     console.log("Runs once on mount!");
   }, []); // No dependency
   ```

---

### **4. Dependency Array Kyu Array Ki Form Mein Hota Hai?**
- Dependency array ek **list of variables or references** hai.
- Array isliye use hota hai kyunki ek hi hook ke andar **multiple dependencies** ko track karna ho sakta hai.

Example:
```jsx
useEffect(() => {
  console.log("Runs when name or age changes!");
}, [name, age]);
```

---

### **5. Dependency Array Mein Functions Kyu Directly Nahi Daalte?**
Dependency array mein functions ko dalne ki problem:
- **JavaScript Functions Are Compared by Reference, Not by Code or Name.**
  - Har render ke saath function ka **naya reference** ban jata hai.
  - Is wajah se React ko lagta hai ki function change ho gaya, aur `useEffect` unnecessarily trigger hota hai.

Example:
```jsx
function App() {
  const chat = () => console.log("Chat clicked!"); // Har render pe naye reference ke saath banega

  useEffect(() => {
    console.log("Effect triggered!");
  }, [chat]); // Always runs, because `chat` reference is new
}
```

Solution:
- Functions ko dependency array mein stable reference ke saath rakhna padta hai. Yeh `useCallback` se hota hai:
  ```jsx
  const chat = useCallback(() => {
    console.log("Chat clicked!");
  }, []); // Stable reference
  ```

---

### **6. React Kaise Changes Detect Karta Hai?**

#### **React Variables Ko "By Value" Compare Karta Hai**
- Primitive values (e.g., numbers, strings, booleans) ko React "by value" compare karta hai. Agar value same hai, toh React bolega **"Koi change nahi hua."**

Example:
```jsx
useEffect(() => {
  console.log("Runs when count changes!");
}, [count]); // React will compare old `count` value vs new `count` value
```

#### **React Functions Ko "By Reference" Compare Karta Hai**
- Functions ya objects ko React "by reference" compare karta hai.  
- **New Reference Means New Dependency**:
  ```jsx
  const func1 = () => console.log("Hello");
  const func2 = () => console.log("Hello");

  console.log(func1 === func2); // false, because reference is different
  ```

- Har render ke saath function ka reference change hota hai, chahe code aur naam same ho.

---

### **7. Declarative vs Imperative Thinking in React**

#### **Declarative Thinking**  
- React mein tum "kya karna hai" batate ho, na ki "kaise karna hai".
- Tum useEffect ko bas yeh bolte ho:
  > *"Jab-jab meri dependency array change ho, tab-tak yeh callback run kar do."*

Example:
```jsx
useEffect(() => {
  console.log("Fetch new data!");
}, [userId]); // React manages when and how to fetch data
```

#### **Imperative Thinking**
- Tum React ko manually har kaam karne ko bolte ho.  
- Example (wrong approach):
  ```jsx
  if (userIdChanged) {
    fetchData(userId);
  }
  ```

Declarative approach React ke lifecycle ko achhe se handle karta hai aur side effects ko isolate karta hai.

---

### **8. `useCallback` and Stabilizing Functions**

React mein `useCallback` ka use hota hai functions ke reference ko **stable** banane ke liye.  
Agar function ka reference stable hai, toh React bolega:
- **"Dependency same hai, useEffect ko dubara mat chalao."**

Example:
```jsx
const chat = useCallback(() => {
  console.log("Chat clicked!");
}, []); // No dependencies -> Stable reference

useEffect(() => {
  console.log("Effect triggered!");
}, [chat]); // Effect will only run when `chat` changes (which it won't)
```

---

### **9. Dependency Array Ke Without Problems**

Agar tum dependency array hi nahi doge ya galat dependencies specify karoge:
1. Infinite Loop:
   ```jsx
   useEffect(() => {
     setState(state + 1); // Keeps running forever
   });
   ```

2. Missing Dependency Warning:
   ```jsx
   useEffect(() => {
     console.log(data);
   }, []); // `data` missing from dependency array
   ```

React yeh warning deta hai taaki tum side effects ko correctly handle kar sako.

---

### **10. Recap of Key Points**

- **useEffect** ek declarative way hai side effects handle karne ka.
- **Dependency Array** React ko batata hai ki kab effect ko run karna hai.
- **Functions Are Compared by Reference**, aur woh har render ke baad change hote hain.
- **useCallback** ka use karke functions ke reference ko stabilize karte hain.
- React ka declarative nature tumhe lifecycle aur rendering manage karne mein madad karta hai.
