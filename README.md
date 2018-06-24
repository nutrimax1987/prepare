console.log('by reference example 1');
let a = {num:22};
let c = b = a;
b = {};
console.log(a); // {num:22}
console.log(b); // {}
console.log(c); // {num:22}

console.log('by reference example 2');

a = {num:55};
c = b = a;
b.num = 10;
console.log(a);  // {num:10}
console.log(b);  // {num:10}
console.log(c);  // {num:10}


console.log('closures example');
var addTo = function (passed){
  var add = function(inner){
    return passed + inner;
  }
  return add;
}

var addNothing = new addTo();
var addThree = new addTo(3);
var addFour = new addTo(4);

console.log(addNothing(1)); // NaN - because passed id 'undefined'
console.log(addThree(1)); // 4 - because passed = 3
console.log(addFour(1)); // 5 - because passed = 4

console.log('indexes example');
const x = [1,2,3];
x[-1] = -45;
console.log(x.indexOf(10000)); // -1
console.log(x[x.indexOf(10000)]); // - 45

console.log('sorting numbers');
let arr = [1,21,5,10,31,15];
console.log(arr.sort()); // same [1,21,5,10,31,15]
console.log(arr.sort((a,b) => a>b))//[1, 5, 10, 15, 21, 31]

console.log('sorting strings');
arr = ['betta','alpha','gamma'];
console.log(arr.sort()); // ["alpha", "betta", "gamma"]


console.log('operators with Number.MIN_VALUE - almoust zero value');
let i = Number.MIN_VALUE; 
console.log(i*i); // 0 
console.log(i+1); // 1
console.log(i-1); // -1
console.log(i/i); // 1


console.log('adding arrays print like strings');
arr = [1,2,3] + [4,5,6];
console.log(arr); // "1,2,34,5,6"

str = String([ ...[1,2,3], ...[4,5,6]]);
console.log(str); // "1,2,3,4,5,6" 

console.log('Number.MAX_SAFE_INTEGER - max length is 16'); 
console.log(555555555555555555); // 555555555555555600 - because 18 digits
console.log(Number.MAX_SAFE_INTEGER);  // 9007199254740991

console.log(NaN === NaN); // false


console.log('IIFE (block scope)- immidiately invoked function expression');
(function(){
   let x = y = 100;
})();
console.log(y); // 100 - y isn't behave correctly, y variable not using 'let', it because global  
console.log(x); // "ReferenceError: x is not defined


var Animal = {kind: 'any'};

Animal.prototype.move = function(){
  console.log('animal runs');  
}

var Cat = {};
Cat = Object.create(Animal);
