
# অবজেক্ট

<info:types> অধ্যায়ে আমরা জেনেছি, জাভাস্ক্রিপ্টে সাতটি ডাটা টাইপ রয়েছে। তাদের মধ্যে ছয়টিকে বলা হয় "প্রিমিটিভ", কারণ তাদের ভ্যালুতে শুধু একটি জিনিসই (হোক তা স্ট্রিং, নাম্বার বা অন্য যেকোনো কিছু) থেকে থাকে।

অন্যদিকে, বিভিন্ন ধরনের ডাটার কালেকশন ও একটু জটিল ধরনের জিনিস রাখার জন্য অবজেক্ট ব্যবহৃত হয়। জাভাস্ক্রিপ্টের প্রতিটি বিষয়ে অবজেক্টের আধিক্য এবং প্রভাব বিদ্যমান। সুতরাং অন্য কিছু নিয়ে গভীরে জানার আগে আমাদের অবশ্যই অবজেক্ট সম্পর্কে জানতে হবে।

দ্বিতীয় বন্ধনী `{…}` ও তার সাথে একগুচ্ছ ঐচ্ছিক *প্রোপার্টি* এর সাহায্যে একটি অবজেক্ট তৈরি করা যায়। একটি প্রপার্টি "key: value" জোড়ায় হয়ে থাকে, যেখানে `key` একটি স্ট্রিং (একে প্রোপার্টির নামও বলা হয়), এবং `value` হতে পারে যেকোনো কিছু।

আমরা অবজেক্টকে তুলনা করতে পারি একটি সাইন করা ফাইলের কেবিনেটের সাথে। যেখানে প্রতিটি ফাইল একটি key (ফাইলের নাম) দিয়ে সংরক্ষণ করা আছে। সুতরাং ফাইলের নাম দিয়ে ফাইল খুঁজে বের করা বা নতুন ফাইল যুক্ত করা অথবা মুছে ফেলা খুবই সহজ।

![](object.svg)

একটি খালি অবজেক্ট ("খালি কেবিনেট"), এ দুটি সিনট্যাক্সের যেকোনো একটি দিয়ে তৈরি করা যায়ঃ

```js
let user = new Object(); // "অবজেক্ট কন্সট্রাক্টর" সিনট্যাক্স
let user = {};  // "অবজেক্ট লিটারেল" সিনট্যাক্স
```

![](object-user-empty.svg)

অবজেক্ট তৈরিতে সচরাচর দ্বিতীয় বন্ধনী `{...}` ব্যবহৃত হয়। এধরণের ডিক্লারেশনকে বলে "অবজেক্ট লিটারেল"।

## লিটারেল এবং প্রোপার্টি

আমরা একই সঙ্গে কিছু প্রোপার্টি "key: value" জোড়ায় `{...}` এর ভেতর দিয়ে দিতে পারিঃ

```js
let user = {     // একটি অবজেক্ট
  name: "John",  // "name" key তে "John" ভ্যালুটি সংরক্ষণ করা হয়েছে
  age: 30        // "age" key তে 30 ভ্যালুটি সংরক্ষণ করা হয়েছে
};
```

কোলনের `":"` আগে প্রোপার্টির key ("নাম" অথবা "আইডেন্টিফায়ার" ও বলা হয়) থাকে এবং এর ডানে একটি ভ্যালু থাকে।

`user` অবজেক্টে দুটো প্রপার্টি আছেঃ

1. প্রথম প্রোপার্টির কী হল `"name"` এবং ভ্যালু `"John"`।
2. দ্বিতীয় প্রোপার্টির নাম হল `"age"` এবং ভ্যালু `30`।

`user` কে এভাবে কল্পনা করা যায়, একটি ফাইলের কেবিনেট যেখানে "name" এবং "age" লেবেলের দুটি সাইন করা ফাইল আছে।

![user object](object-user.svg)

আমরা যেকোনো সময় ফাইল যুক্ত করা, মুছে দেয়া বা পড়তে পারি।

প্রোপার্টির ভ্যালুগুলো ডট নোটেশন দিয়ে এক্সেস করা যায়ঃ

```js
// অবজেক্ট থেকে প্রোপার্টি ভ্যালু গুলো নেয়া হচ্ছেঃ
alert( user.name ); // John
alert( user.age ); // 30
```

ভ্যালুগুলো যেকোনো টাইপের হতে পারে। একটি বুলিয়ান প্রোপার্টি যুক্ত করা যাকঃ

```js
user.isAdmin = true;
```

![user object 2](object-user-isadmin.svg)

কোন একটা প্রোপার্টিকে মুছে দিতে আমরা `delete` অপারেটরটি ব্যবহার করতে পারিঃ

```js
delete user.age;
```

![user object 3](object-user-delete.svg)

আমরা প্রোপার্টির নাম হিসেবে একাধিক শব্দও ব্যবহার করতে পারি, তবে সেক্ষেত্রে শব্দগুলো উদ্ধৃতি চিহ্নের ভেতর রাখতে হবেঃ

```js
let user = {
  name: "John",
  age: 30,
  "likes birds": true  // একাধিক শব্দের প্রোপার্টির নাম অবশ্যই উদ্ধৃতি চিহ্নের ভেতর রাখতে হবে
};
```

![](object-user-props.svg)


শেষ প্রোপার্টিটি একটি কমা দিয়ে শেষ হতে পারেঃ
```js
let user = {
  name: "John",
  age: 30*!*,*/!*
}
```
একে বলা হয় "ট্রেইলিং" বা "হ্যাঙ্গিং" কমা। এটি এড/রিমুভ এবং পরিবর্তন করা সহজ করে, কারণ সবগুলো লাইন দেখতে একই রকম হয়।

## তৃতীয় বন্ধনী

একাধিক শব্দের প্রোপার্টি গুলোকে ডট দিয়ে এক্সেস করা যায় নাঃ

```js run
// এটি একটি সিনট্যাক্স এরর দেখাবে
user.likes birds = true
```

এটার কারণ, ডট নোটেশন ব্যবহার করার জন্য key - কে একটি ভেরিয়েবল আইডেন্টিফায়ার হতে হবে। যার জন্য এতে কোন স্পেস থাকতে পারবে না এবং আরও অন্যান্য নিয়ম রয়েছে।

তৃতীয় বন্ধনী ব্যবহার করে আরেকটি পদ্ধতি রয়েছে, যা যেকোনো স্ট্রিং এ কাজ করেঃ

```js run
let user = {};

// set
user["likes birds"] = true;

// get
alert(user["likes birds"]); // true

// delete
delete user["likes birds"];
```

এখন সবকিছু কাজ করে। বন্ধনীর ভেতর স্ট্রিংটি ঠিকমত উদ্ধৃতি চিহ্নের ভেতর রয়েছে (যেকোনো উদ্ধৃতি চিহ্ন কাজ করবে)।

লিটারেল স্ট্রিং এর বিপরীতে তৃতীয় বন্ধনী ব্যবহারের পদ্ধতিটি এক্সপ্রেশনের রেসাল্টকে ব্যবহার করে প্রোপার্টির নাম বের করার সুযোগ দেয় -- যেমনটা নিচের ভেরিয়েবল থেকেঃ

```js
let key = "likes birds";

// same as user["likes birds"] = true;
user[key] = true;
```

এখানে, `key` ভেরিয়েবলটি রান-টাইমে ক্যালকুলেট করে বা ইউজারের ইনপুট এর উপর ভিত্তি করে তৈরি হতে পারে। এবং পরে আমরা এটাকে প্রোপার্টি এক্সেস করার জন্য ব্যবহার করতে পারি। এটি প্রোগ্রাম করার সময় খুব ভাল স্বাধীনতা দেয়।

যেমনঃ

```js run
let user = {
  name: "John",
  age: 30
};

let key = prompt("What do you want to know about the user?", "name");

// ভেরিয়েবলের মাধ্যমে এক্সেস করা হচ্ছে
alert( user[key] ); // John (if enter "name")
```

ডট নোটেশনকে একই ভাবে ব্যবহার করা যায় নাঃ

```js run
let user = {
  name: "John",
  age: 30
};

let key = "name";
alert( user.key ) // আনডিফাইন্ড
```

### কম্পুটেড প্রোপার্টি

আমরা অবজেক্ট লিটারেলে তৃতীয় বন্ধনী ব্যবহার করতে পারি। একে বলে *কম্পিউটেড প্রোপার্টি*।

উদাহরণস্বরূপঃ

```js run
let fruit = prompt("Which fruit to buy?", "apple");

let bag = {
*!*
  [fruit]: 5, // প্রোপার্টির নাম fruit ভেরিয়েবল থেকে নেয়া হয়েছে
*/!*
};

alert( bag.apple ); // 5 if fruit="apple"
```

কম্পিউটেড প্রোপার্টির মানে খুবই সহজঃ `[fruit]` মানে প্রোপার্টির নামটি `fruit` ভেরিয়েবল থেকে নেয়া হবে।

সুতরাং, যদি ভিজিটর `"apple"` লিখে, `bag` হয়ে যাবে `{apple: 5}`।

মূলত, নিচের কোডটিও একই কাজ করেঃ
```js run
let fruit = prompt("Which fruit to buy?", "apple");
let bag = {};

// প্রোপার্টির নাম fruit ভেরিয়েবল থেকে নাও
bag[fruit] = 5;
```

...কিন্তু আগেরটি দেখতে সুন্দর।

আমরা তৃতীয় বন্ধনীর ভেতরে আরও জটিল এক্সপ্রেশন ব্যবহার করতে পারিঃ

```js
let fruit = 'apple';
let bag = {
  [fruit + 'Computers']: 5 // bag.appleComputers = 5
};
```

তৃতীয় বন্ধনী ডট নোটেশনের চাইতে অনেক বেশী পশক্তিশালী। কিন্তু তাদের লেখাটা একটু কষ্টকর।

সুতরাং অধিকাংশ সময়, যখন প্রোপার্টির নাম সহজ এবং আগে থেকেই জানা, ডট নোটেশন ব্যবহৃত হয়। এবং যদি আমাদের জটিল কিছু করতে হয়, তখন আমরা তৃতীয় বন্ধনী ব্যবহার করি।



````smart header="সংরক্ষিত শব্দগুলো প্রোপার্টির নাম হিসেবে ব্যবহার করা যায়"
ভেরিয়েবল এর নাম ভাষা কর্তৃক সংরক্ষিত শব্দ, যেমন "for", "let", "return" ইত্যাদি হতে পারবে না।

কিন্তু অবজেক্টের প্রোপার্টির জন্য তেমন কোন বাধ্যবাধকতা নেই। যেকোনো নাম ব্যবহার করা যায়ঃ

```js run
let obj = {
  for: 1,
  let: 2,
  return: 3
};

alert( obj.for + obj.let + obj.return );  // 6
```

মূলত, যেকোনো নাম ব্যবহার করা যায়, কিন্তু একটি বিশেষ নাম আছেঃ `"__proto__"` যেটি ঐতিহাসিক কারণে বিশেষভাবে ব্যবহৃত হয়। যেমন, আমরা এটি অবজেক্ট নয় এমন কোন ভ্যালুতে ব্যবহার করে পারি নাঃ

```js run
let obj = {};
obj.__proto__ = 5;
alert(obj.__proto__); // [object Object], didn't work as intended
```

যেমনটি আমরা কোডে দেখতে পাচ্ছি, প্রিমিটিভ `5` এর সাথে সংযুক্তিটি উপেক্ষা করা হয়েছে।

যদি আমরা ইচ্ছামত কী ভ্যালু একটি অবজেক্টে রাখতে যাই, এবং ভিজিটরদের কী প্রদান করতে দিতে দেই, তাহলে এটির কারণে অনেক বাগ এবং এমনকি ভলনারেবিলিটির উৎস তৈরি হতে পারে।

এরকম ক্ষেত্রে ভিজিটর `__proto__` কে কী হিসেবে দিয়ে দিতে পারে, এবং এসাইনমেন্ট এর লজিকটা নষ্ট হয়ে যেতে পারে (যেমনটা উপড়ে দেখানো হয়েছে)।

অবজেক্টকে `__proto__` কে সাধারণ প্রোপার্টি হিসেবে গণ্য করতে বাধ্য করা যায়, যা আমরা পরে দেখব, কিন্তু তার আগে আমাদের অবজেক্ট সম্পর্কে আরও জানতে হবে।

[Map](info:map-set) নামে আরও একটি ডাটাস্ট্রাকচার রয়েছে, যেটি সম্পর্কে আমরা <info:map-set> অধ্যায়ে জানব, যা যেকোনো কী গ্রহণ করে।
````


## প্রোপার্টি ভ্যালু সর্টহ্যান্ড

প্রায়সময় আমরা বর্তমানে বিদ্যমান ভেরিয়েবলগুলোকে প্রোপার্টি নামের ভ্যালু হিসেবে ব্যবহার করি।

যেমনঃ

```js run
function makeUser(name, age) {
  return {
    name: name,
    age: age
    // ...অন্যান্য প্রোপার্টি
  };
}

let user = makeUser("John", 30);
alert(user.name); // John
```

উপরের উদাহরণে, প্রোপার্টি এবং ভেরিয়েবলের নাম একই। এই ব্যবহারটি এত বেশী হয়ে থাকে যে একটি বিশেষ *প্রোপার্টি ভ্যালু সর্টহ্যান্ড* আছে এটিকে ছোট করে লিখার জন্য।

`name:name` এর পরিবর্তে আমরা সরাসরি `name` লিখতে পারি, এরকম ভাবেঃ

```js
function makeUser(name, age) {
*!*
  return {
    name, // same as name: name
    age   // same as age: age
    // ...
  };
*/!*
}
```

আমরা একই অবজেক্টে একই সাথে সাধারণ প্রোপার্টি এবং সর্টহ্যান্ড ব্যবহার করতে পারিঃ

```js
let user = {
  name,  // same as name:name
  age: 30
};
```

## প্রোপার্টি আছে কিনা পরীক্ষা করা

অবজেক্টের একটি উল্লেখযোগ্য ফিচার হল এর যেকোনো প্রোপার্টিকে এক্সেস করা যায়। যদি প্রোপার্টি না থাকে তাহলে কোন এরর হয় না! অবজেক্টে নেই এমন প্রোপার্টিকে এক্সেস করলে শুধু `undefined` রিটার্ন করে। প্রোপার্টি আছে কিনা নেই পরীক্ষার জন্য এটি একটি সাধারণ উপায় দেয় -- যা হল আনডিফাইন্ড এর সাথে তুলনা করাঃ

```js run
let user = {};

alert( user.noSuchProperty === undefined ); // true মানে "এরকম কোন প্রোপার্টি নেই"
```

একটি বিশেষ অপারেটর `"in"` ও রয়েছে প্রোপার্টি আছে কিনা পরীক্ষা করার জন্য।

সিনট্যাক্সঃ
```js
"key" in object
```

যেমনঃ

```js run
let user = { name: "John", age: 30 };

alert( "age" in user ); // true, user.age আছে
alert( "blabla" in user ); // false, user.blabla নেই
```

মনে রাখবেন `in` অপারেটরের বাম পাশে অবশ্যই একটি  "প্রোপার্টির নাম" থাকতে হবে। সাধারণত এটিকে উদ্ধৃতি চিহ্নের ভেতর রাখা হয়।

উদ্ধৃতি চিহ্ন না দিলে এটিকে একটি ভেরিয়েবল হিসেবে ধরা হবে, এবং ওই ভেরিয়েবলের ভ্যালুর সাথে তুলনা করা হবে। যেমনঃ

```js run
let user = { age: 30 };

let key = "age";
alert( *!*key*/!* in user ); // true, key থেকে নামটি নিয়ে, ওই নামে প্রোপার্টি আছে কিনা দেখা হচ্ছে
```

````smart header="`undefined` প্রোপার্টির ক্ষেত্রে \"in\" এর ব্যবহার"
সাধারণত, `"=== undefined"` এভাবে প্রোপার্টি আছে কিনা পরীক্ষা করা ঠিকঠাক কাজ করে, কিছু বিশেষ ক্ষেত্রে এটি ভুল ফলাফল দেয়, কিন্তু `"in"` অপারেটর ঠিকমত কাজ করে।

এটি ঘটে যখন অবজেক্টের প্রোপার্টি আছে কিন্তু তা `undefined` ঃ

```js run
let obj = {
  test: undefined
};

alert( obj.test ); // এটি undefined, তাই - প্রোপার্টি নেই?

alert( "test" in obj ); // true, প্রোপার্টি আছে!
```


উপরের কোডে, `obj.test` এই প্রোপার্টি কিন্তু টেকনিক্যালি অবজেক্টে আছে। সুতরাং `in` অপারেটর ঠিকভাবে কাজ করছে।

এধরেন পরিস্থিতি কিছুটা বিরল, কারণ `undefined` আসলে এসাইন করা হয় না। আমরা বেশীরভাগ সময় "অজানা" বা "খালি" বুঝাতে `null` ব্যবহার করি। তাই `in` অপারেটরের ব্যবহার কদাচিৎ দেখা যায়।
````

## "for..in" লুপ

অবজেক্টের সবগুলো কী এর উপর ভিজিট করার জন্য একটি বিশেষ ধরণের লুপ আছেঃ `for..in`। এটি `for(;;)` এর চাইতে পুরোপুরি আলাদা, যেটি আমরা পূর্বে দেখেছি।

সিনট্যাক্সঃ

```js
for (key in object) {
  // অবজেক্টের প্রতিটি কী এর জন্য এই বডিটি এক্সিকিউট হবে
}
```

যেমন, `user` এর সব প্রোপার্টি বের করা যাকঃ

```js run
let user = {
  name: "John",
  age: 30,
  isAdmin: true
};

for (let key in user) {
  // keys
  alert( key );  // name, age, isAdmin
  // values for the keys
  alert( user[key] ); // John, 30, true
}
```

উল্লেখ্য, সব "for" লুপ কন্সট্রাক্ট, লুপের মধ্যে লুপিং ভেরিয়েবল ঘোষণা করতে দেয়, যেমন এখানে `let key`।

এছাড়াও, আমরা এখানে `key` এর পরিবর্তে অন্য ভেরিয়েবলও ব্যবহার করতে পারব। উদাহরণস্বরূপ, `"for (let prop in obj)"` এটিও ব্যপকভাবে ব্যবহৃত হয়।


### অবজেক্ট এ প্রোপার্টির অর্ডার

আমরা যদি অবজেক্টের উপর লুপ চালাই, আমরা কি সবগুলো প্রোপার্টি একই ভাবে সাজানো পাবো যেভাবে আমরা সংযুক্ত করেছি? আমরা কি এই বিষয়ে ভরসা রাখতে পারি?

সংক্ষেপে বললেঃ "বিশেষ ভাবে সাজানো" ঃ  যেসব প্রোপার্টি ইন্টেজার সেসব ক্রমানুসারে সাজানো, অন্যেরা তৈরি করার সময় যে অর্ডারে ছিল সেই অর্ডারে সাজানো পাওয়া যাবে। বিস্তারিত নিচে।

উদাহরণ হিসেবে, ধরি ফোন কোডের একটি অবজেক্টঃ

```js run
let codes = {
  "49": "Germany",
  "41": "Switzerland",
  "44": "Great Britain",
  // ..,
  "1": "USA"
};

*!*
for (let code in codes) {
  alert(code); // 1, 41, 44, 49
}
*/!*
```

এই অবজেক্টটি হয়তো ইউজারকে একটি অপশনের লিস্ট দেখানোর জন্য ব্যবহার করা হবে। যদি সাইটটি মূলত জার্মান ইউজারদের জন্য হয়, তাহলে আমরা চাইব `49` যেন প্রথমেই থাকে।

কিন্তু কোড রান করলে আমরা পুরোপুরি অন্যরকম অবস্থা দেখিঃ

- USA (1) goes first
- then Switzerland (41) and so on.

ফোন কোডগুলো ঊর্ধ্বগামী (ascending) ক্রমে সাজানো, কারণ তারা ইন্টিজার। তাই আমরা পাই `1, 41, 44, 49`।

````smart header="ইন্টিজার প্রোপার্টি?"
"ইন্টিজার প্রোপার্টি" হল একটি স্ট্রিং যেটি ইন্টিজার (পূর্ণসংখ্যা) থেকে বা ইন্টিজারে কোন পরিবর্তন ছাড়াই পরিবর্তন করা যায়।

তাই, "49" একটি ইন্টিজার প্রোপার্টির নাম, কারণ যখন এটিকে ইন্টিজারে পরিবর্তন এবং ইন্টিজার থকে স্ট্রিং এ পরিবর্তন করা হয় এটি একই থাকে। কিন্তু "+49" এবং "1.2" ইন্টিজার নয়ঃ

```js run
// Math.trunc is a built-in function that removes the decimal part
alert( String(Math.trunc(Number("49"))) ); // "49", same, integer property
alert( String(Math.trunc(Number("+49"))) ); // "49", not same "+49" ⇒ not integer property
alert( String(Math.trunc(Number("1.2"))) ); // "1", not same "1.2" ⇒ not integer property
```
````

...অপরদিকে, যদি কী ইন্টিজার না হয়, তাহলে তারা তৈরির সময় যে ক্রমে ছিল সেভাবেই থাকবে, যেমনঃ

```js run
let user = {
  name: "John",
  surname: "Smith"
};
user.age = 25; // add one more

*!*
// যদি কী ইন্টিজার না হয়, তাহলে তারা তৈরির সময় যে ক্রমে ছিল সেভাবেই থাকবে
*/!*
for (let prop in user) {
  alert( prop ); // name, surname, age
}
```

তাই, ফোন কোডের ইস্যু ঠিক করতে আমরা একটু "ধূর্ততার" সাহায্য নিতে পারি। প্রতিটি কোডের আগে `"+"` চিহ্ন ব্যবহার করে তাদের নন-ইন্টিজার করে দেয়াই যথেষ্ট।

এভাবেঃ

```js run
let codes = {
  "+49": "Germany",
  "+41": "Switzerland",
  "+44": "Great Britain",
  // ..,
  "+1": "USA"
};

for (let code in codes) {
  alert( +code ); // 49, 41, 44, 1
}
```

এখন যেভাবে কাজ করা উচিত সেভাবেই কাজ করছে।

## রেফারেন্সের মাধ্যমে কপি করা

অবজেক্ট আর প্রিমিটিভ এর মধ্যে একটি মৌলিক পার্থক্য হল, অবজেক্ট রেফারেন্সের ("by reference") মাধ্যমে সংরক্ষণ এবং কপি করা হয়।

প্রিমিটিভ ভ্যালুগুলোঃ স্ট্রিং, নাম্বার, বুলিয়ান -- এসব সংরক্ষণ এবং কপি হয়ে থাকে সম্পূর্ণ/সরাসরি ভ্যালু হিসেবে।

উদাহরণঃ

```js
let message = "Hello!";
let phrase = message;
```

এর ফলে, আমাদের কাছে দুটি স্বাধীন ভেরিয়েবল আছে, যাদের প্রত্যেকে `"Hello!"` স্ট্রিংটি সংরক্ষণ করে।

![](variable-copy-value.svg)

অবজেক্টগুলো এই রকম না।

**ভেরিয়েবল সরাসরি অবজেক্টকে সংরক্ষণ করে না, অবজেক্টের "মেমোরি এড্রেস", বা অবজেক্টের "রেফারেন্স" সংরক্ষণ করে।**

এখানে অবজেক্টটির গঠনের ছবি দেয়া হলঃ

```js
let user = {
  name: "John"
};
```

![](variable-contains-reference.svg)

এখানে, অবজেক্টটি মেমোরিতে কোথাও সংরক্ষিত রয়েছে। এবং `user` ভেরিয়েবলের কাছে এই অবজেক্টের "রেফারেন্স" রয়েছে।

**যখন একটি অবজেক্ট ভেরিয়েবলকে কপি করা হয় -- রেফারেন্সটি কপি হয়। অবজেক্টটি দ্বিতীয়বার তৈরি হয় না।**

অবজেক্টকে যদি কেবিনেট ধরি, তাহলে ভেরিয়েবলের কাছে এর চাবি থাকে। ভেরিয়েবল কপি করা মানে চাবি কপি করা, পুরো কেবিনেটকে কপি করা নয়।

উদাহরণস্বরূপঃ

```js no-beautify
let user = { name: "John" };

let admin = user; // রেফারেন্স কপি হচ্ছে
```

এখন আমাদের কাছে দুটি ভেরিয়েবল আছে, প্রত্যেকের কাছে একই অবজেক্টের রেফারেন্স আছেঃ

![](variable-copy-reference.svg)

আমরা যেকোনো ভেরিয়েবল ব্যবহার করে কেবিনেটকে এক্সেস এবং এর কন্টেন্টকে মডিফাই করতে পারিঃ

```js run
let user = { name: 'John' };

let admin = user;

*!*
admin.name = 'Pete'; // "admin" রেফারেন্সের মাধ্যমে পরিবর্তন করা হচ্ছে
*/!*

alert(*!*user.name*/!*); // 'Pete', "user" রেফারেন্সের মাধ্যমে পরিবর্তনটা দেখা হচ্ছে
```

উপরের উদাহরণটি প্রমাণ করে যে শুধু একটিই অবজেক্ট রয়েছে। অনেকটা যেন আমাদের কাছে একই কেবিনেটের দুইটা চাবি আছে এবং একটা চাবি (`admin`) ব্যবহার করা হয়েছে কেবিনেট খুলার জন্য। এরপর, আমরা যদি অন্য চাবি (`user`) ব্যবহার করি, আমরা কি পরিবর্তন হয়েছে তা দেখতে পাই।

### রেফারেন্সের সাহায্যে তুলনা

ইকুয়ালিটি `==` and স্ট্রিক্ট ইকুয়ালিটি `===` অপারেটর অবজেক্টের জন্য একই ভাবে কাজ করে।

**দুটি অবজেক্ট ইকুয়াল বা সমান হবে শুধুমাত্র তারা যদি একই অবজেক্ট হয়ে থাকে।**

যেমন, যদি দুটি ভেরিয়েবলের রেফারেন্স একই অবজেক্টকে পয়েন্ট করে, তাহলে তারা সমানঃ

```js run
let a = {};
let b = a; // copy the reference

alert( a == b ); // true, দুটি ভেরিয়েবলে একই অবজেক্টের পয়েন্ট রাখা আছে
alert( a === b ); // true
```

এবং এখানে দুটি আলাদা অবজেক্ট দেখানো হচ্ছে যারা সমান না, যদিও দুটিই খালি অবজেক্ট।

```js run
let a = {};
let b = {}; // দুটি আলাদা অবজেক্ট

alert( a == b ); // false
```

`obj1 > obj2` এ রকম তুলনা বা প্রিমিটিভের সাথে তুলনা `obj == 5` এর সময় অবজেক্ট প্রিমিটিভে রূপান্তরিত হয়। আমরা শীঘ্রই অবজেক্ট কিভাবে রূপান্তর হয় তা জানব, কিন্তু সত্যি বলতে, এরকম তুলনা বাস্তবে খুবই কম প্রয়োজন হয় এবং সাধারণত কোডে ভুলের কারণে হয়ে থাকে।

### Const object

An object declared as `const` *can* be changed.

For instance:

```js run
const user = {
  name: "John"
};

*!*
user.age = 25; // (*)
*/!*

alert(user.age); // 25
```

It might seem that the line `(*)` would cause an error, but no, there's totally no problem. That's because `const` fixes only value of `user` itself. And here `user` stores the reference to the same object all the time. The line `(*)` goes *inside* the object, it doesn't reassign `user`.

The `const` would give an error if we try to set `user` to something else, for instance:

```js run
const user = {
  name: "John"
};

*!*
// Error (can't reassign user)
*/!*
user = {
  name: "Pete"
};
```

...But what if we want to make constant object properties? So that `user.age = 25` would give an error. That's possible too. We'll cover it in the chapter <info:property-descriptors>.

## Cloning and merging, Object.assign

So, copying an object variable creates one more reference to the same object.

But what if we need to duplicate an object? Create an independent copy, a clone?

That's also doable, but a little bit more difficult, because there's no built-in method for that in JavaScript. Actually, that's rarely needed. Copying by reference is good most of the time.

But if we really want that, then we need to create a new object and replicate the structure of the existing one by iterating over its properties and copying them on the primitive level.

Like this:

```js run
let user = {
  name: "John",
  age: 30
};

*!*
let clone = {}; // the new empty object

// let's copy all user properties into it
for (let key in user) {
  clone[key] = user[key];
}
*/!*

// now clone is a fully independent clone
clone.name = "Pete"; // changed the data in it

alert( user.name ); // still John in the original object
```

Also we can use the method [Object.assign](mdn:js/Object/assign) for that.

The syntax is:

```js
Object.assign(dest, [src1, src2, src3...])
```

- Arguments `dest`, and `src1, ..., srcN` (can be as many as needed) are objects.
- It copies the properties of all objects `src1, ..., srcN` into `dest`. In other words, properties of all arguments starting from the 2nd are copied into the 1st. Then it returns `dest`.

For instance, we can use it to merge several objects into one:
```js
let user = { name: "John" };

let permissions1 = { canView: true };
let permissions2 = { canEdit: true };

*!*
// copies all properties from permissions1 and permissions2 into user
Object.assign(user, permissions1, permissions2);
*/!*

// now user = { name: "John", canView: true, canEdit: true }
```

If the receiving object (`user`) already has the same named property, it will be overwritten:

```js
let user = { name: "John" };

// overwrite name, add isAdmin
Object.assign(user, { name: "Pete", isAdmin: true });

// now user = { name: "Pete", isAdmin: true }
```

We also can use `Object.assign` to replace the loop for simple cloning:

```js
let user = {
  name: "John",
  age: 30
};

*!*
let clone = Object.assign({}, user);
*/!*
```

It copies all properties of `user` into the empty object and returns it. Actually, the same as the loop, but shorter.

Until now we assumed that all properties of `user` are primitive. But properties can be references to other objects. What to do with them?

Like this:
```js run
let user = {
  name: "John",
  sizes: {
    height: 182,
    width: 50
  }
};

alert( user.sizes.height ); // 182
```

Now it's not enough to copy `clone.sizes = user.sizes`, because the `user.sizes` is an object, it will be copied by reference. So `clone` and `user` will share the same sizes:

Like this:
```js run
let user = {
  name: "John",
  sizes: {
    height: 182,
    width: 50
  }
};

let clone = Object.assign({}, user);

alert( user.sizes === clone.sizes ); // true, same object

// user and clone share sizes
user.sizes.width++;       // change a property from one place
alert(clone.sizes.width); // 51, see the result from the other one
```

To fix that, we should use the cloning loop that examines each value of `user[key]` and, if it's an object, then replicate its structure as well. That is called a "deep cloning".

There's a standard algorithm for deep cloning that handles the case above and more complex cases, called the [Structured cloning algorithm](https://html.spec.whatwg.org/multipage/structured-data.html#safe-passing-of-structured-data). In order not to reinvent the wheel, we can use a working implementation of it from the JavaScript library [lodash](https://lodash.com), the method is called [_.cloneDeep(obj)](https://lodash.com/docs#cloneDeep).



## Summary

Objects are associative arrays with several special features.

They store properties (key-value pairs), where:
- Property keys must be strings or symbols (usually strings).
- Values can be of any type.

To access a property, we can use:
- The dot notation: `obj.property`.
- Square brackets notation `obj["property"]`. Square brackets allow to take the key from a variable, like `obj[varWithKey]`.

Additional operators:
- To delete a property: `delete obj.prop`.
- To check if a property with the given key exists: `"key" in obj`.
- To iterate over an object: `for (let key in obj)` loop.

অবজেক্টকে রেফারেন্সের মাধ্যমে এসাইন বা কপি করা হয়। In other words, a variable stores not the "object value", but a "reference" (address in memory) for the value. So copying such a variable or passing it as a function argument copies that reference, not the object. All operations via copied references (like adding/removing properties) are performed on the same single object.

"আসলেই কপি" (ক্লোন) করার জন্য আমরা `Object.assign` অথবা  [_.cloneDeep(obj)](https://lodash.com/docs#cloneDeep) ব্যবহার করতে পারি।

আমরা এই অধ্যায়ে যা জেনেছি তাকে "প্লেইন অবজেক্ট", বা শুধু  or `Object` বলা হয়।

জাভাস্ক্রিপ্টে অনেক অন্যান্য অবজেক্ট রয়েছেঃ

- `Array` ডাটা কালেকশন সংরক্ষণের জন্য,
- `Date` তারিখ ও সময় সংক্রান্ত তথ্য সংরক্ষণের জন্য,
- `Error` এরর সম্পর্কিত তথ্য সংরক্ষণের জন্য,
- ...ইত্যাদি।

তাদের কিছু বিশেষ বৈশিষ্ট্য আছে যা আমরা পরে জানব। মাঝে মাঝে অনেকে "Array type" বা "Date type" বলে, কিন্তু এসব নিজেরা কোন আলাদা টাইপ না, এগুলো সব "অবজেক্ট" ডাটা টাইপ। এবং তাদের নানা ভাবে বর্ধিত করা হয়েছে।

জাভাস্ক্রিপ্ট এ অবজেক্ট খুবই পাওয়ারফুল। আমরা অনেক বড় একটি বিষয় সংক্ষিপ্তভাবে আলোচনা করেছি। আমরা অবজেক্ট নিয়ে প্রচুর কাজ করব এবং এই টিউটেরিয়ালের অন্যান্য অংশে অবজেক্ট সম্পর্কে আরও জানব।
