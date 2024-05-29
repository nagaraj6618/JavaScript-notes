# JavaScript Object

## Object Intro
```js
const person = {
   name:'Nagaraj s',
   age:18,
   displayName : function() {
      return this.name;
   },
   name:'Nagaraj'
};

//create property by using Objectname.Property = '';
person.email = 'nagaraj516700@gmail.com';
person.email = {
   domain:'gmail',
   mailId : person.email,
}

person.getNameLength = function() {
   try{
      return this.name.length;
   }
   catch(e){
      return -1;
   }
}


//calling object property function;
const nameOfPerson = person.displayName();
console.log(nameOfPerson);


//Accesscing 

//objectName['property'];
console.log(person['displayName']());
console.log(person['getNameLength']());

//objectName[expression];
let functionName = 'displayName';
console.log(person[functionName]());



```

## Object Methods

### assing()
```js

//1.) Object.assign(source,target);

It is a static method copies all property from source to target and return new target.

*/
const source = {
   a:1,b:2
};

const target = {
   b:4,c:3
};

const newTarget = Object.assign(target,source); // { a: 1, b: 4, c: 3 }
console.log(newTarget);

// the return target and assing target will be equal..
console.log(target == newTarget); // true..

// newTarget = Object.assign(target,newTarget); //Reassignment is not posible due to const.so it's throws an error,but its posiible in let or var.

//Object.assing(target,source1,source2,.....,sourcen);

//cloning or Coping an object using assign method.

const cloneObject = Object.assign({},target);
console.log(cloneObject);

//merging multipe object using assign;

const obj1 = {a:1};
const obj2 = {b:2};
const obj3 = {c:3};

Object.assign(obj1,obj3,obj2);
console.log(obj1);

// null and undefined are ignored.

Object.assign(obj1,null,undefined);
console.log(obj1);
```
### Object Constructor

```js

//constructor
console.log(obj1.constructor());


obj1.constructor= function(name){
   return name;
}
console.log(obj1.constructor("Hello world"));

//Declare object using constructor;
const newObj = new Object({
   a:'a',
   b:'b'
});
console.log(newObj);

```