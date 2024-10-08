# JavaScript ES6 / Scrimba

## Template Literals

Template literals, JavaScript'te verileri stringler ile birlikte daha kolay kullanmak için geliştirilmiş bir yöntemdir.

**Örnek:**

```jsx
let str1 = "hello";
let str2 = "world";

console.log(`${str1} ${str2}`);

// Daha zor kullanım= console.log(str1 + " " + str2);

```

---

## Destructuring Objects

Destructuring objects, JavaScript'te object veri tipinin kullanımını oldukça kolaylaştıran bir kullanım şeklidir. Obje içinde tanımlanan key'ler başka değişkende değişken ismi olarak tanımlanır ve değişken değeri de obje ismi olarak ayarlanır.

**Örnek**:

```jsx
const player = {
  name: 'LeBron James',
  club: 'LA Lakers',
  address: {
    city: 'Los Angeles'
  }
};

console.log(player.address.city);

const { name, club } = player;

console.log(name);
console.log(club);

```

Obje içindeki objelere erişmek için de bu şekilde bir kullanım bulunmaktadır:

```jsx
const player = {
  name: 'LeBron James',
  club: 'LA Lakers',
  address: {
    city: 'Los Angeles'
  }
};

const { name, club, address: { city } } = player;

console.log(`${name} lives in ${city}`);

```

### Destructuring Objects Challenge

```jsx
/*
    **** Challenge ****

    For this challenge, destructure the following object.
*/

const student = {
    name: "Kyle",
    age: 24,
    projects: {
        diceGame: "Two player dice game using JavaScript"
    }
};

const { name, age, projects: { diceGame } } = student;

console.log(name);
console.log(age);
console.log(diceGame);

```

---

## Destructuring Arrays

Destructuring, objects'e benzer olarak arraylerin kullanımını kolaylaştıran bir yöntemdir:

**Örnek**:

```jsx
// Destructuring Arrays Mantığı
let names = ['Bedirhan', 'Coding God', 'KURT'];
let [firstName, middleName, lastName] = names;

console.log(lastName); // 'KURT'

// Asıl kullanım:
let [firstName, middleName, lastName] = ['Bedirhan', 'Coding God', 'KURT'];

console.log(lastName); // 'KURT'

```

---

## Object Literals

Object literals, fonksiyonlarda dublikasyon kod yazımının önüne geçen bir kullanım şeklidir. Bu kullanıma göre atama yapılacağında parametre adı ile atama yapılan değer adı aynı ise sadece parametre adını yazmak yeterlidir.

**Örnek**:

```jsx
function addressMaker(city, state) {
    const newAddress = { city: city, state: state };

    console.log(newAddress);
}

addressMaker('Austin', 'Texas');

// Bu iki kullanım aslında aynıdır ve ikinci kullanım Object Literal kullanılarzk yazıldığından dublikasyon kodun önüne geçilmiştir.

function addressMaker(city, state) {
    const newAddress = { city, state };

    console.log(newAddress);
}

addressMaker('Austin', 'Texas');

// Çıktı: { city: 'Austin', state: 'Texas' }

```

---

## For of Loop

For of loop yapısı ile bir dizi içindeki elemanlar sırayla teker teker alınarak bunlar üzerinde işlem yapılabilir.

**Örnek:**

```jsx
let fullName = "Bedirhan KURT";

for (const char of fullName) {
    console.log(char);
}
```

### For of Loop Challenge

```jsx
// Challenge - For Of Loop

// Using the For of Loop, iterate through the array and print into the console a message like:
// Tom lives in Lisbon

const students = [
    { name: "John", city: "New York" },
    { name: "Peter", city: "Paris" },
    { name: "Kate", city: "Sydney" }
];

// Solution:

for (let student of students) {
    console.log(`${student.name} lives in ${student.city}`);
}
```

---

## Spread Operator

Spread operator'u yeni bir değişken oluşturulacakken başka bir değişken referans olacaksa, o değişkenin orijinal halini alır ve referans değişkenin değeri değişse bile sonradan oluşturulan değişkenin değeri değişmez.

**Örnek:**

```jsx
let persons = ["Ali", "Ahmet", "Mehmet"];
let friends = persons;

persons.push("Arif");

console.log(friends); // "Ali", "Ahmet", "Mehmet", "Arif"

// Spread Operator ile Kopyalama
let persons = ["Ali", "Ahmet", "Mehmet"];
let friends = [...persons];

persons.push("Arif");

console.log(friends); // "Ali", "Ahmet", "Mehmet"

// Yani, yeni oluşturulan değişken referans olarak atanan değişkenin ilk değerini tutuyor ve veriyi statik olarak değiştirmiyor.

// Spread Operator Alternatif Kullanım
let persons = ["Ali", "Ahmet", "Mehmet"];
let friends = ["Hasan", ...persons, "Hüseyin"];

persons.push("Arif");

console.log(friends); // "Hasan", "Ali", "Ahmet", "Mehmet", "Hüseyin"

```

## Spread Operator Challenge

```jsx
/*
    **** Challenge ****

    Imagine you are going out to do some grocery shopping.
    So you have an array called shoppingList with all the products you want to buy.

    Now that you are inside the shop, you have a basket with all the products from your list, but you want to add a few more.

    Create a new array called shoppingBasket, that will be a copy of the shoppingList array, and add some new products into it.
*/

const shoppingList = ["eggs", "milk", "butter"];

// Çözüm
const shoppingBasket = [...shoppingList, "olive", "tomato"];

console.log(shoppingBasket); // ["eggs", "milk", "butter", "olive", "tomato"]

```

---

# Rest Operator

**ES6'daki "rest" operatörü** (`...`), fonksiyonlara esneklik kazandırmak için kullanılır ve bilinmeyen sayıda argümanı bir dizi olarak toplar. Bu, bir fonksiyonun aldığı parametre sayısının sabit olmadığı durumlarda oldukça yararlıdır. Rest operatörü, bir fonksiyonun parametre listesinde son sırada yer almalıdır.

**Rest Operatörünün Kullanımı:**

Fonksiyonlarda birden fazla argümanı tek bir dizi içinde toplamak için kullanılır.

**Örnek:**

```jsx
function topla(...sayilar) {
    return sayilar.reduce((toplam, sayi) => toplam + sayi, 0);
}

console.log(topla(1, 2, 3)); // 6 çıktısı verir
console.log(topla(10, 20, 30, 40)); // 100 çıktısı verir

```

Bu örnekte, `...sayilar` ifadesi, fonksiyona gönderilen tüm argümanları bir diziye dönüştürür ve `reduce` yöntemi bu sayıları toplar.

**Önemli Noktalar:**

- Rest operatörü son parametre olmalıdır. Başka parametreler de olabilir, ancak rest operatöründen sonra başka bir parametre gelmemelidir.

**Örnek:**

```jsx
function topla(...sayilar) {
    let toplam = 0;
    for (let sayi of sayilar) {
        toplam += sayi;
    }
    return toplam;
}

console.log(topla(1, 2, 3));  // Çıktı: 6
console.log(topla(5, 10));    // Çıktı: 15

```

```jsx
function carpma(carpan, ...sayilar) {
    return sayilar.map(sayi => sayi * carpan);
}

console.log(carpma(2, 1, 2, 3)); // [2, 4, 6]

```

Bu örnekte, `carpan` ilk argüman olarak alınır ve geri kalan tüm argümanlar `...sayilar` olarak diziye aktarılır.

**Spread Operatöründen Farkı:**

- **Rest operatörü**: Argümanları **toplar**.
- **Spread operatörü**: Elemanları **yayar** (örneğin, bir dizi veya objeyi yayarak tek tek elemanlar halinde kullanır).

Rest operatörü, özellikle değişken sayıda argümanla çalışmayı kolaylaştırır ve fonksiyonların daha esnek olmasını sağlar.

---

# Arrow Functions

Arrow fonksiyonu daha kolay bir fonksiyon tanımlama türüdür. Kullanımı şu şekildedir:

```jsx
// Function declaration
function breakfastMenu() {
    return "I'm going to scrambled eggs for breakfast";
}

// Anonymous function
const lunchMenu = function() {
    return "I'm going to eat pizza for lunch";
}

// Arrow function
const dinnerMenu = () => {
    return "I'm going to eat a burger for dinner";
}

dinnerMenu();

// Arrow Function (Parametre ile)
const dinnerMenuWithFood = (food) => {
    return `I'm going to eat a ${food} for dinner`;
}

console.log(dinnerMenuWithFood("chicken salad"));

// Sadece return etme işlemi yapacaksa süslü parantezler olmadan da bu şekilde kullanılabilir:
const dinnerMenuCompact = (food) => `I'm going to eat a ${food} for dinner`;

// Sadece bir parametre varsa parantez kullanılmasına gerek yoktur.
const dinnerMenuSingleParam = food => `I'm going to eat a ${food} for dinner`;

```

---

# Default Params

Fonksiyonlarda parametrelere eklenebilecek varsayılan değerlere verilen addır. Bu şekilde eğer fonksiyon tanımlanırken parametre alacak şekilde tanımlanmışsa ancak fonksiyon çağrılırken parametre olmadan çağrılmışsa, fonksiyonun kendinde tanımlı olan değer `undefined` olmak yerine varsayılan değere atanır.

**Örnek**:

```jsx
const leadSinger = (name = "bro") => {
    console.log(`Hello ${name}!`);
}

leadSinger(); // Çıktı: "Hello bro!"

```

## Default Params Challenge

```jsx
/*
**** Challenge *****

Create a function that receives a parameter of food.
If your parameter food is going to have a value of "milk"
the function should print into the console the following:

"I'm going to buy milk from the grocery shop"

But if you don't pass a value to your parameter food, it should print
"I'm going to buy something from the grocery shop"
*/

const shopping = (food = "something") => `I'm going to buy ${food} from the grocery shop`;

console.log(shopping()); // "I'm going to buy something from the grocery shop"

```

---

# Includes Fonksiyonu

`includes` fonksiyonu ile bir değerin bir array veya dizi içinde olup olmadığı kontrol edilebilir ve sonuç boolean olarak döner.

**Örnek**:

```jsx
const array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

console.log(array.includes(5)); // True
console.log(array.includes(15)); // False

```

## Includes Challenge

```jsx
/*
    ** includes() Challenge
        * You want to make a chocolate cake
        * And you have a list of ingredients represented with an array
        * Using the JavaScript includes() function
        * Check if you have the ingredient chocolate in your list of ingredients, and print into the console "We are going to make a chocolate cake" if you have it
        * Else print into the console "We can't make a chocolate cake because we are missing the ingredient chocolate"
*/

const listIngredients = ["flour", "sugar", "eggs", "butter"];

if (listIngredients.includes("chocolate")) {
    console.log("We are going to make a chocolate cake.");
} else {
    console.log("We can't make a chocolate cake because we are missing the ingredient chocolate.");
}
```

---

# Let & Const

JavaScript'te üç temel veri tanımlama biçimi vardır: `var`, `let` ve `const`. `var` değişkenleri hoisting (taşıma) sebebiyle fonksiyon veya statement içinde bile tanımlansa global scope'a taşınır. `let` ve `const` ise kendi scopelarında kullanılır; ancak `let` değişkenlerinin değerleri değiştirilebilirken, `const` değişkenlerinin değerleri genellikle değiştirilemez.

**Örnek**:

```jsx
if (false) {
    var example = 5;
}

console.log(example); // undefined

/*
Yukarıdaki satır şuna eşittir:

if (false) {
    let example = 5;
}

console.log(example); // ReferenceError: example is not defined
*/
```

---

# Import and Export

- **Amaç:** Bir dosyadan (modülden) fonksiyonları, değişkenleri veya sınıfları diğer dosyalara erişilebilir hale getirmek için kullanılır.
- **İki Türü Vardır:**
    1. **Named Exports (İsimli İhracatlar):** Birden fazla değişken veya fonksiyonun tek bir dosyadan dışarı aktarılmasını sağlar.
    
    ```jsx
    // module.js
    export const myVar = "Hello";
    export function myFunction() {
        console.log("This is a function");
    }
    
    ```
    
    1. **Default Export (Varsayılan İhracat):** Bir dosyadan yalnızca bir değişken veya fonksiyonun varsayılan olarak dışa aktarılmasını sağlar.
    
    ```jsx
    // module.js
    const myDefaultFunction = () => {
        console.log("Default function");
    };
    export default myDefaultFunction;
    
    ```
    
    `export default`, bir dosyanın ana içeriğini dışa aktarmak için kullanılır. Bu içerik, import edilirken herhangi bir isimle çağrılabilir. Bir dosyada yalnızca bir default export olabilir, ancak farklı isimlerle import edilebilir. `export default`, dosyanın en önemli içeriğini temsil eder ve genellikle esneklik sağlar.
    

**`import`**

- **Amaç:** Başka bir dosyadan (modülden) daha önce dışa aktarılan fonksiyonları, değişkenleri veya sınıfları almak için kullanılır.
- **İki Türü Vardır:**
    1. **Named Imports (İsimli İthalatlar):** İsimli dışa aktarılan öğeleri almak için kullanılır.
    
    ```jsx
    // main.js
    import { myVar, myFunction } from './module.js';
    console.log(myVar); // "Hello"
    myFunction();       // "This is a function"
    
    ```
    
    1. **Default Import (Varsayılan İthalat):** Varsayılan olarak dışa aktarılan öğeyi almak için kullanılır.
    
    ```jsx
    // main.js
    import myDefaultFunction from './module.js';
    myDefaultFunction(); // "Default function"
    
    ```
    

**Neden Kullanılır?**

1. **Modülerlik:** Kodunuzu daha düzenli ve anlaşılır hale getirir.
2. **Bakım Kolaylığı:** Her modül belirli bir işlevselliğe sahiptir, bu da kodun bakımını kolaylaştırır.
3. **Yeniden Kullanılabilirlik:** Modüller farklı yerlerde tekrar kullanılabilir, bu da kodunuzu daha verimli hale getirir.

**`import`** ve **`export`**, JavaScript'te modüler bir yapı oluşturmanın temel yollarıdır. Bu, kodunuzu daha yönetilebilir, okunabilir ve hatasız hale getirir.

**Varsayılan Olarak Dışa Aktarılan (Default Export)**

Varsayılan dışa aktarma, bir modülden yalnızca bir tane olan, fakat farklı isimlerle içe aktarılabilen bir değişken, fonksiyon veya sınıfı belirtmek için kullanılan bir özelliktir. Bir modül varsayılan bir dışa aktarma içeriyorsa, o modülü içe aktarırken belirli bir isim kullanmanıza gerek kalmaz; istediğiniz ismi verebilirsiniz. İşte daha detaylı bir açıklama:

**Varsayılan Dışa Aktarma Nedir?**

**Tanım:** Bir modülde yalnızca bir tane varsayılan dışa aktarma olabilir. Bu, diğer modüllerde bu öğeyi içe aktarırken istediğiniz ismi kullanabileceğiniz anlamına gelir.

**Nasıl Kullanılır?**

1. **Varsayılan Dışa Aktarma Tanımlama:**
    
    ```jsx
    // module.js
    const myFunction = () => {
        console.log("This is the default function");
    };
    
    export default myFunction; // Varsayılan olarak dışa aktarılıyor
    
    ```
    
2. **Varsayılan Dışa Aktarmayı İçe Aktarma:**
    
    ```jsx
    // main.js
    import anyName from './module.js'; // İstediğiniz ismi verebilirsiniz
    anyName(); // "This is the default function"
    
    ```
    

**Anahtar Noktalar:**

1. **Sadece Bir Tane:** Her modülde yalnızca bir tane varsayılan dışa aktarma olabilir.
2. **İstediğiniz İsim:** Varsayılan dışa aktarmayı içe aktarırken, istediğiniz herhangi bir isim kullanabilirsiniz. Bu, diğer dışa aktarılan öğelerden farklı olarak daha esneklik sağlar.

**Örnek:**

Varsayılan dışa aktarma ile birlikte, bir modülde daha fazla öğe dışa aktarmak da mümkündür:

```jsx
// module.js
const myFunction = () => {
    console.log("This is the default function");
};

const anotherFunction = () => {
    console.log("This is another function");
};

export default myFunction; // Varsayılan dışa aktarma
export { anotherFunction }; // İsimli dışa aktarma

```

```jsx
// main.js
import myFunc from './module.js'; // Varsayılan dışa aktarma
import { anotherFunction } from './module.js'; // İsimli dışa aktarma

myFunc(); // "This is the default function"
anotherFunction(); // "This is another function"

```

**Varsayılan Dışa Aktarma**, JavaScript'te bir modülden tek bir ana öğeyi tanımlamak için etkili bir yoldur. Bu, daha esnek ve anlaşılır bir modül yapısı oluşturmanıza olanak tanır.

---

## Import & Export Challenge

```jsx
/**Challenge**

Inside the file data.js, create a function add that will receive 2 numbers and return the sum of them. Make sure to export this function.

- Import the function add into the index.js file.
- Create a variable result that will hold the result of the function add when you call it and pass 2 numbers into it.
- Print into the console the value of the variable result;

// data.js:
const add = (num1, num2) => num1 + num2; */

export {add};

// index.js:
import {add} from "./data.js";

const result = add(1, 2);
console.log(result);
```

---

# padStart() & padEnd()

Bir değişkene herhangi bir değer belli bir limite kadar eklemek için kullanılır. Baştan ekleme ve sondan ekleme yapılabilir.

```jsx
let example = 'Bedirhan';

console.log(example.padEnd(10, 'a')); // Bedirhanaaa

// Yukarıdaki kodda verinin uzunluğu 10 oluncaya kadar pad işlemi devam ediyor.

```

---

# Classes

Sınıflar, obje oluşturmak için kullanılan bir şablon veya tanımlama biçimidir. İçerisinde **constructor** ve **methods** olarak iki ana bölüm bulunur.

**Örnek**:

```jsx
export class Animal {
    constructor(type, legs) {
        this.type = type;
        this.legs = legs;
    }

    makeNoise(sound = 'Loud Noise') {
        console.log(sound);
    }
}

```

Bir başka önemli konu ise **static**'tir. Static aslında bir fonksiyon tanımıdır, ancak bu tanımla birlikte tanımlanan fonksiyon, sınıf için bir örnek oluşturmadan çalıştırılabilir. Instance yani örnek ile static çağrılamaz; sadece orijinal sınıf üzerinden çağrılabilir.

**Örnek**:

```jsx
export class Animal {
    constructor(type, legs) {
        this.type = type;
        this.legs = legs;
    }

    makeNoise(sound = 'Loud Noise') {
        console.log(sound);
    }

    static return10() {
        return 10;
    }
}

console.log(Animal.return10()); // Bu kod çıktı verir.

console.log(Animal.makeNoise()); // Bu kod hata verir.

```

Bir başka özellik ise **get** özelliğidir. Get sayesinde sınıf için bir özellik oluşturulur. Fonksiyon yapısı ile oluşturulur ama parantez olmadan çalışır:

```jsx
class Circle {
    constructor(radius) {
        this._radius = radius; // Yarıçap, alt çizgi ile başlar
    }

    // Getter metodu ile alan hesaplama
    get area() {
        return Math.PI * this._radius * this._radius; // Alan formülü: πr²
    }
}

// Kullanım örneği
const myCircle = new Circle(5); // Yarıçapı 5 olan bir daire oluştur
console.log(`Dairenin alanı: ${myCircle.area}`); // Output: Dairenin alanı: 78.53981633974483

```

**Extend classes** özelliği ise bir sınıfı genişletmek veya o sınıfı temel alarak yeni bir sınıf oluşturmak için kullanılır.

**Örnek**:

```jsx
export class Cat extends Animal {
    makeNoise(sound = "meow") {
        console.log(sound);
    }
}

// Burada Cat olarak yeni bir sınıf oluşturulmuş oldu.

```

**Constructor**'ı genişletmek için ise `super` kelimesi kullanılır. Bu şekilde üst sınıfla aynı olan özellikler çağrılır:

```jsx
export class Cat extends Animal {
    constructor(type, legs, tail) {
        super(type, legs);
        this.tail = tail;
    }
}
```

---

## Classes Challange

```jsx
/**Classes Challenge**:

Create a class Player with the following:
- Add a Name and Country properties
- Add a function that when it runs should print into the console ("Messi was born in Argentina");
- Make sure to adapt this function to receive dynamic Names and Clubs.

Create a Subclass called TennisPlayer that extends from the class Player
- Add a new property Age.
- Add a function that when it runs should print into the console something similar ("Rafael Nadal is 34 years old and knows how to play Tennis");
- Make sure the Name and Age are dynamic.*/

class Player {
    constructor(name, country) {
        this.name = name;
        this.country = country;   
    }
    
    playerInfo() {
        console.log(`${this.name} is from ${this.country}.`);
    }
}

class TenisPlayer extends Player {
    constructor(name, country, age){
        super(name, country)
        this.age = age
    }
    
    tenisPlayerInfo() {
        console.log(`${this.name} is from ${this.country} and ${this.age} years old.`);
    }
}

const messi = new Player("Messi", "Argentina");
messi.playerInfo();

const ronaldo = new TenisPlayer("ronaldo", "russia", "18")
ronaldo.tenisPlayerInfo()
```

---

# Trailing Commas

ES6 ile birlikte fonksiyon parametreleri veya array itemlerinin sonundaki virguller artık bir error sebebi değil.

**Örnek**:

```jsx
function selam(isim,) {}

// veya

const liste = [1, 2, 3,]
```

---

# Promises

**JavaScript'te Promise Yapısı**

**Promise Nedir?**

Promise, JavaScript'te asenkron işlemleri yönetmek için kullanılan bir yapıdır. Asenkron işlemlerin sonuçlarını temsil eder ve üç durumda bulunabilir: `pending` (beklemede), `fulfilled` (tamamlandı), ve `rejected` (reddedildi).

**Promise Sınıfı**

```jsx
class Promise {
    constructor(executor) {
        // Asenkron işlemi gerçekleştiren kod
        // executor: resolve ve reject fonksiyonlarını alır
    }

    then(onFulfilled, onRejected) {
        // Promise başarıyla tamamlandığında çağrılır
    }

    catch(onRejected) {
        // Promise hata aldığında çağrılır
    }
}

```

**Promise Kullanımı**

```jsx
const myPromise = new Promise((resolve, reject) => {
    const success = true; // İşlemin sonucunu simgeler

    if (success) {
        resolve("Başarılı sonuç!"); // Promise tamamlandığında çağrılır
    } else {
        reject("Hata oluştu!"); // Hata durumunda çağrılır
    }
});

// Sonucu işleme
myPromise
    .then(result => console.log(result)) // "Başarılı sonuç!" yazdırır
    .catch(error => console.log(error)); // Hata durumunda yazdırılır

```

**`then()` ve `catch()`**

- `then()`, `resolve()` çağrıldığında iletilen değeri alır.
- `catch()`, `reject()` çağrıldığında hata mesajını yakalar.

**Neden `if/else` Yerine `Promise` Kullanılır?**

`Promise`, asenkron işlemlerin daha yönetilebilir olmasını sağlar. Eğer sadece `if/else` kullanılsaydı, işlemler birbirine zincirlenemezdi ve kodun okunabilirliği düşerdi. `Promise`, asenkron işlemlerin başarılı ya da başarısız sonuçlarını daha düzenli bir şekilde yönetmeyi mümkün kılar.

## Promises Challange

```jsx
/**
 * Promises - Challenge
 * Create a promise that returns some user data and throws an error when not found.
 * Log the user data when listening to the promise as well as log the error.
 *
 * Docs - <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise>
*/

let users = ["Ali", "Ahmet", "Hasan", "Huseyin",]
let givenUsername = "Ali"

const checkUser = new Promise ((resolve, reject) => {
    if (users.includes(givenUsername)) {
        resolve("User found.")
    } else {
        reject("User not found!")
    }
})

checkUser.then(resolve => console.log(resolve)).catch(error => console.log("error"))

```

---

# Fetch

Fetch API, web tarayıcılarında HTTP istekleri yapmak için kullanılan bir JavaScript özelliğidir. Aşağıda verdiğiniz kod üzerinden Fetch API'nin nasıl çalıştığını adım adım açıklayalım:

**1. Fetch İsteği**

```jsx
fetch('<https://jsonplaceholder.typicode.com/comments>', {
    method: "POST",
    body: JSON.stringify({
        postId: 1,
        name: 'Dylan',
        email: 'dylansemail310@gmail.com',
        body: 'That was dope!'
    })
})

```

- **`fetch()` Fonksiyonu:** Belirtilen URL'ye (bu durumda bir API) bir istek gönderir.
- **`method`:** İsteğin türünü belirler. Burada "POST" ile veri gönderiyoruz.
- **`body`:** Gönderilecek veriyi belirtir. `JSON.stringify()` ile bir JavaScript nesnesini JSON formatına çevirir.

**2. İstek Yanıtını İşleme**

```jsx
.then(response => response.json())

```

- **`then()`:** İstek tamamlandığında çalışacak bir fonksiyon tanımlar. İlk `then` bloğunda, gelen `response` nesnesini alır.
- **`response.json()`:** Yanıtı JSON formatında çözümleyerek bir Promise döndürür. Bu, veriyi daha kullanışlı bir forma getirir.

**3. Çözümleme Sonucu**

```jsx
.then(data => console.log(data))

```

- İkinci `then` bloğu, önceki `then`'den dönen JSON verisini alır ve konsola yazdırır.

**Özet**

- Fetch API, HTTP istekleri yapmanıza ve yanıtları işleyerek asenkron veri elde etmenizi sağlar.
- `fetch()` fonksiyonu, bir URL'ye istek gönderir, ardından gelen yanıtı çözümleyerek kullanılabilir bir formata dönüştürür.
- Bu işlem, `then()` metodları ile zincirlenerek kolayca yönetilebilir.

## Fetch Challange

```jsx
/**
 * Fetch - Challenge
 *
 * GET the first comments value '<https://jsonplaceholder.typicode.com/comments/1>' and log its value.
 * POST a new comment using '<https://jsonplaceholder.typicode.com/comments>' and log its value.
 *
 * RESTFul API Guide - <https://jsonplaceholder.typicode.com/guide.html>
 * Docs - <https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch>
 */

fetch('<https://jsonplaceholder.typicode.com/comments/1>')
    .then((response) => response.json())
    .then((data) => console.log(data))

fetch('<https://jsonplaceholder.typicode.com/comments>', {
        method: 'POST',
        body: JSON.stringify({
            name: 'Comment 105',
            email: 'dylansemail310@gmail.com',
            body: 'Dopes comment in the game',
            postId: 1
        })
    })
    .then((response) => response.json())
    .then((data) => console.log(data))

```

---

# Async & Await

Normalde JavaScript kodun başından sonuna doğru tüm satırları sırayla run eder çalışır. Ancak sonucu beklemez. Sadece run eder ve sonraki satıra devam eder. Eğer satırdaki işlemin tamamlanması uzun sürüyorsa ileride o satırdaki işlemden faydalanan kodlar için problemli bir durum oluşabilir. Bu problem Async & await fonksiyonları ile mevcut satırın işlemi tamamlandıktan sonra bir sonraki satıra geçilerek çözülebilir.

**Örnek**:

```jsx
const photos = [];

async function photoUpload() {
    let uploadStatus = new Promise( (resolve, reject) => {
        setTimeout( () => {
            photos.push("Profile Pic");
            resolve("Photo Uploaded")
        }, 3000)
    })

    let result = await uploadStatus;

    console.log(result);
    console.log(photos.length);
}

photoUpload();

// Eğer async ve await olmasaydı photos.length 0 olacaktı çünkü bu log işlemi photoUpload fonksiyonu tamamlanıp listeye item eklenmeden önce yapılıyordu.

```

## Async & Await Challange

```jsx
//Challenge - Async & Await

//Print on the console a random joke from the Chuck Norris API using Fetch and Async and Await

const apiUrl = "<https://api.chucknorris.io/jokes/random>";

async function getJoke(url) {
    const response = await fetch(url);
    const data = await response.json();

    console.log(data);
}

getJoke(apiUrl)

```

---

# Sets in ES6

JavaScript'te **Set**, benzersiz değerlerin bir koleksiyonunu temsil eden bir veri yapısıdır. Set'ler, aynı değerin birden fazla kez bulunmasına izin vermez ve sıralı bir yapı sunar. Temel özellikleri şunlardır:

1. **Benzersizlik**: Her bir değer yalnızca bir kez depolanır. Aynı değeri birden fazla kez eklemeye çalışırsanız, sadece bir kopyası tutulur.
2. **Sıralama**: Set içinde eklenen değerler, eklenme sırasına göre saklanır.
3. **Dinamik**: Set'lere eleman ekleyebilir, çıkarabilir ve bunları kontrol edebilirsiniz.

**Temel Kullanım**

- **Set Oluşturma**:
    
    ```jsx
    const mySet = new Set();
    
    ```
    
- **Değer Ekleme**:
    
    ```jsx
    mySet.add(1);
    mySet.add(2);
    mySet.add(1); // 1 zaten var, eklenmez
    
    ```
    
- **Değer Kontrolü**:
    
    ```jsx
    console.log(mySet.has(1)); // true
    console.log(mySet.has(3)); // false
    
    ```
    
- **Değer Silme**:
    
    ```jsx
    mySet.delete(1); // 1 silinir
    
    ```
    
- **Set'in Boyutu**:
    
    ```jsx
    console.log(mySet.size); // 1
    
    ```
    
- **Set'i Temizleme**:
    
    ```jsx
    mySet.clear(); // Tüm değerler silinir
    
    ```
    

**Örnek:**

```jsx
const numbers = new Set([1, 2, 3, 4, 5]);
numbers.add(6);
numbers.add(2); // 2 zaten var, eklenmez

console.log(numbers); // Set(6) { 1, 2, 3, 4, 5, 6 }

```

Set'ler, dizilere göre bazı avantajlar sunar, özellikle benzersiz değerlerin yönetiminde ve sıklıkla bulunan öğelerin performans açısından kontrol edilmesinde yararlıdır.
