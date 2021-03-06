# ডাইন্যামিক ইমপোর্ট

আগের অধ্যায়ে আমরা ইমপোর্ট এবং এক্সপোর্ট নিয়ে আলোচনা করেছি যাদের "static" বলা হয়। যার সিনট্যাক্স খুবই সাধারন। 

প্রথমত, `import` এর কোন প্যারামিটার ডাইনামিক ভাবে আমরা জেনারেট করতে পারি না। 

মডিউলের পাথ অবশ্যই প্রিমিটিভ স্ট্রিং হতে হবে, ফাংশন কল হওয়া যাবে না। এটি কাজ করবে নাঃ 

```js
import ... from *!*getModuleName()*/!*; // এরর, শুধুমাত্র "string" প্রযোজ্য
```

দ্বিতীয়ত, আমরা কন্ডিশনালি অথবা রান-টাইমে ইমপোর্ট করতে পারবো না।

```js
if(...) {
  import ...; // এরর, এটি প্রযোজ্য নয়।
}

{
  import ...; // এরর, আমারা কোন ব্লকের মধ্যে ইমপোর্ট রাখতে পারি না। 
}
```

তার কারন `import`/`export` এর উদ্দেশ্য হচ্ছে কোডের গঠনে মেরুদন্ডের ন্যায় কাজ করা। এটি একটি ভালো দিক, কোডের গঠন বিশ্লেষণ করে দেখা যায়, একটি বিশেষ টুলের দ্বারা মডিউল গুলোকে ফাইলে একসাথে রাখা যায়, অব্যবহৃত এক্সপোর্ট গুলো রিমুভ("tree-shaken") করা যায়. `imports/exports` এর সাধারন গঠনের কারনেই এটি সম্ভব হয়।

কিন্তু, প্রয়োজনে একটি মডিউলকে কিভাবে আমরা ডাইনামিকালি ইমপোর্ট করতে পারি? 

## import() এক্সপ্রেশন 

`import(module)` এক্সপ্রেশনটি মডিউলকে লোড করে এবং একটি প্রমিস রিটার্ন করে যা একটি মডিউল অবজেক্টের মধ্যে রিসল্ভ হয়ে থাকে এবং এতে সমস্ত এক্সপোর্ট গুলো থাকে। 

আমরা কোডের যে কোন জায়গায় এটি ডাইনামিকালি ব্যবহার করতে পারি, যেমনঃ 

```js
let modulePath = prompt("কোন মডিউলটি লোড করতে চান?");

import(modulePath)
  .then(obj => <module object>)
  .catch(err => <লোডিং এরর, যদি কোন মডিউল না থাকে>)
```

অথবা, যদি এটি একটি `async` ফাংশনের ভিতর হয়ে থাকে তবে  `let module = await import(modulePath)` ব্যবহার করতে পারি। 

যেমন, আমাদের যদি নিম্নলিখিত মডিউল থাকে `say.js`: 

```js
// 📁 say.js
export function hi() {
  alert(`Hello`);
}

export function bye() {
  alert(`Bye`);
}
```

...তবে ডাইনামিক ইমপোর্টটি হতে পারেঃ 

```js
let {hi, bye} = await import('./say.js');

hi();
bye();
```

অথবা, যদি `say.js` এর ডিফল্ট এক্সপোর্ট থাকেঃ 

```js
// 📁 say.js
export default function() {
  alert("মডিউল লোড হয়েছে (export default)!");
}
```

...তারপর এটাকে এক্সেস করার জন্য আমরা মডিউল অব্জেক্টের `default` প্রপার্টি ব্যাবহার করতে পারি। 

```js
let obj = await import('./say.js');
let say = obj.default;
// অথাবা, এক লাইনে: let {default: say} = await import('./say.js');

say();
```

এখানে সম্পূর্ণ উদাহারনটি রয়েছেঃ

[codetabs src="say" current="index.html"]

```smart
রেগুলার স্ক্রিপ্টে ডাইনামিক ইমপোর্ট কাজ করে, তার জন্য `script type="module" প্রয়োজন হয় না।
```

```smart
যদিও `import()` দেখতে ফাংশন কলের মতো, কিন্তু এটি একটি (`super()` মতো) বিশেষ সিন্টেক্স যার জন্য "parentheses" ব্যবহার করতে হয়। `).

তাই আমারা `import` কে কোন ভেরিয়েবলে কপি অথবা `call/apply` করতে পারি না।
```
