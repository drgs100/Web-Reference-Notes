# Objects 

Object is a collection of propertes. A property of an object can be explained as a variable that is attached to the object. 

You can access the properties with simple dot-notation.

```js
objectName.propertyName
```

You can define a propery by assigining it a value. Unassigned properties of an object are ```undefined``` (not ```null```). 

```js
var myCar = new Object();
myCar.make = "Ford";
myCar.model = "Mustang";
myCar.year = 1969;
myCar.noPropert; // undefined
```

Objects can also be accessed or set using a bracket notation.

```js
myCar["make"] = "Ford";
myCar["model"] = "Mustang";
myCar["year"] = 1969;
```

## Create new objects

You can create with the object initilizer or create a construcor function and then instantiate an object using that function and the ```new``` operator.

### Object initilizer

Also called literal notaion.

```js
var obj = {
  "prop_1": "value_1",
  "prop_2": "value_2",
  "prop_3": "value_2"
};
```

### Constructor function

```js
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}

var myCar = new Car("Eagle", "Talon TSi", 1993);

// Objects can have a property that is another object

function Person(name, age, sex) {
  this.name = name;
  this.age = age;
  this.sex = sex;
}

var rand = new Person("Rand McKinnin", 33, "M");
var ken = new Person("Ken Jones", 39, "M");

function Car(make, model, year, owner) {
  this.make = make;
  this.model = model;
  this.year = year;
  this.owner = owner;
}

var car1 = new Car("Eagle", "Talon TSi", 1993, rand);
```

### ```Object.create``` method

Allows you to choose the prototype object you want to create, without having to define a constructor function.

```js
var Animal = {
  type: "Invertebrates", // Default value of properties
 displayType : function() { // Method which will display type of Animal
   console.log(this.type);
 } 
}

// Create new animal called animal1
var animal1 = Object.create(Animal);
animal1.dislayType(); // Output:Invertebrates

// Create new animal type called Fishes
var fish = Object.create(Animal);
fish.type = "Fishes";
fish.displayType(); // Output: Fishes
```