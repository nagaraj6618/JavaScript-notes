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

### Create()

```js 
// Create Method in object.
/*
 create method is a static method , it uses the existing object as the prototype of the newly created object. 
 
*/
const obj1 = {
   name:'Nagaraj s',
   age:20,
   getName : function(){
      return this.name;
   },
   getEmail: function(){
      return this.email;
   }
};

const newObj = Object.create(obj1);

console.log(newObj) // {}
newObj.email = 'nagaraj516700@gmail.com';

console.log(newObj);

//but it can hold the property and value of existing obj 

console.log(newObj.name);

//New Object and Existing Objects are not equal.

console.log(newObj === obj1);

/*
 Actually Create method creates the new object with the help of existing object ,it can hold the property of existing object  
*/



```

### defineProperties() & defineProperty()
```js 
/* defineProperties()  
 
It is a static method ,it helps to add or change the properties and it mainly used for getter and setter function.


*/
const obj = {
   name:'object',
   follows:10,
};


const newObj = Object.defineProperties(obj,{
   likes:{
      value:100,
      enumerable:true,
      writable:true,
      configurable:true
   }
});
console.log(obj) //{name:'object',follows:10} it will not print the likes ,but it have the likes property 
console.log(obj.likes);
console.log(newObj)

obj.likes = 30;
console.log(obj.likes);

//configuring the property
Object.defineProperty(obj,'likes',{
   
      enumerable:false
   
})
console.log(obj);
//Add setter and getter function

Object.defineProperties(obj,{
   getter:{
      value:function(){
         return obj.name;
      },
      enumerable : false,
      configurable:true,
   },
   setter:{
      value:function(name){
         obj.name = name;
      },
      enumerable:true,
      configurable:true,
   }
});

console.log(obj.getter());

console.log(obj); 

obj.setter("Nagaraj S");

console.log(obj.getter());

console.log(obj);

Object.defineProperty(obj,'getter',{
   get(){
      return this.name
   }
});
Object.defineProperties(obj,{
   getter:{
      get(){
         return this.name;
      },
      enumerable:false,
   },
   setter:{
      set(name){
         this.name = name;
      },
      
   }
})
console.log(obj);

console.log(obj.getter);
obj.setter = "Hello World"
console.log(obj.getter);

Object.defineProperty(obj,'length',{
   get(){
      return this.name.length;
   },
   enumerable:false,
   configurable:false,
   
})

console.log(obj);
console.log(obj.length);


for (i in obj){
   console.log(obj[i]);
}


```

### entries() & formEntries()
```js

/*
   Object.entries()

   It is a static method .It converts in into array format and return the arrays.It follows numerical order.
*/


const obj = {
   name:'Object',
   follows:10,
   likes:0,
   '10':20,
   '1':30
}

const entry1 = Object.entries(obj);

console.log(entry1);//[[ '1', 30 ],[ '10', 20 ],[ 'name', 'Object' ],[ 'follows', 10 ],[ 'likes', 0 ]]
console.log(typeof entry1); //Array Object

const entry2 = Object.entries("foo");

console.log(entry2);//[ [ '0', 'f' ], [ '1', 'o' ], [ '2', 'o' ] ]

/* Object.formEntries()

   It is a static method .It get the array input and return the object form.It is opposite to Object.entries().


*/

console.log(Object.fromEntries(entry1)); // { '1': 30, '10': 20, name: 'Object', follows: 10, likes: 0 }



```

### freeze()
```js
/* Object.freeze()
   It is a static method ,which is used to freeze or can not to change /add the properties and values.It return the same objects.
*/

const obj = {
   name:'nagaraj s',
   age:20,
};

Object.freeze(obj);
console.log(Object.freeze(obj)) //{ name: 'nagaraj s', age: 20 }
obj.age = 30; //throws error if it in strict mode.
obj.follows = 50; //throws error if it in strict mode.

console.log(obj.age); //20 

console.log(obj)//{ name: 'nagaraj s', age: 20 }
```
### getOwnPropertyDescriptor() and getOwnPropertyDescriptors()

```js
/* 
   getOwnPropertyDescriptor() & getOwnPropertyDescriptors();

   It is a static Method ,It is return the description of the property .
*/

const obj = {
   name:'nagaraj s',
   age:23,
}

console.log(obj);
Object.defineProperties(obj,{
   getter:{
      get(){
         return this.name;
      },
      enumerable:true,
      configurable:false,
   }
});

console.log(obj.getter);
const descriptor = Object.getOwnPropertyDescriptors(obj);

console.log(descriptor);

/*
{
  name: {
    value: 'nagaraj s',
    writable: true,
    enumerable: true,
    configurable: true
  },
  age: { value: 23, writable: true, enumerable: true, configurable: true },
  getter: {
    get: [Function: get],
    set: undefined,
    enumerable: true,
    configurable: false
  }
 
 */

const ageDescriptor = Object.getOwnPropertyDescriptor(obj,'age');

console.log(ageDescriptor); //{ value: 23, writable: true, enumerable: true, configurable: true }


```