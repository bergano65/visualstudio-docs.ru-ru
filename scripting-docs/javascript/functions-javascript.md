---
title: "Функции (JavaScript) | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: intrinsic JavaScript functions
ms.assetid: e2a72b5a-3edd-43d8-95e8-91721b38c1c1
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd5626af6417b5f0010545874bd15c86b30a303a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="functions-javascript"></a>Функции (JavaScript)
Функции [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] выполняют действия, а также могут возвращать значения. Иногда это результаты вычислений или сравнения. Функции также называют "глобальными методами".  
  
 Функции объединяют несколько операций под одним именем. Это позволяет оптимизировать код. Можно написать набор операторов, присвоить ему имя, а затем выполнять весь набор, вызывая его и передавая ему необходимые данные.  
  
 Чтобы передать данные в функцию, заключите их в скобки, расположенные после имени функции. Фрагменты данных, передаваемые в функцию, называются аргументами или параметрами. Некоторые функции не принимают никаких аргументов, тогда как другие принимают один или несколько аргументов. В некоторых функциях число аргументов зависит от способа использования функции.  
  
 В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] поддерживаются два типа функций: встроенные в язык и создаваемые пользователями.  
  
## <a name="built-in-functions"></a>Встроенные функции  
 Язык [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] включает в себя несколько встроенных функций. Некоторые из них позволяют обрабатывать выражения и специальные символы, другие служат для преобразования строк в числовые значения.  
  
 Дополнительные сведения об этих встроенных функциях см. в статье [Методы JavaScript](../javascript/reference/javascript-methods.md).  
  
## <a name="creating-your-own-functions"></a>Создание собственных функций  
 Можно создать собственные функции и использовать их по мере необходимости. Определение функции состоит из оператора function и блока операторов [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 Функция **checkTriplet**, показанная в следующем примере, принимает в качестве аргументов длины сторон треугольника. По ним она определяет, является ли данный треугольник прямоугольным. Для этого функция проверяет, составляют ли переданные стороны пифагоров треугольник (то есть равен ли квадрат гипотенузы сумме квадратов двух других сторон). При выполнении проверки функция checkTriplet вызывает две другие функции.  
  
 Обратите внимание на использование очень маленького числа (epsilon) в качестве эталонной переменной в варианте проверки для чисел с плавающей запятой. Если нельзя с уверенностью гарантировать, что все три проверяемых значения являются целыми числами, то целесообразно не использовать прямую проверку сторон на соответствие пифагорову треугольнику из-за неопределенностей и округлений, возникающих при вычислении чисел с плавающей запятой. Поскольку прямая проверка является более точной, код в данном примере определяет, является ли она допустимой, и в случае положительного ответа использует ее.  
  
```JavaScript  
var epsilon = 0.00000000001; // Some very small number to test against.  
  
// The test function for integers.  
function integerCheck(a, b, c)   
{  
   // The test itself.  
   if ( (a*a) == ((b*b) + (c*c)) )     
      return true;  
  
   return false;  
} // End of the integer checking function.  
  
// The test function for floating-point numbers.  
function floatCheck(a, b, c)     
{  
   // Make the test number.  
   var delta = ((a*a) - ((b*b) + (c*c)))  
  
   // The test requires the absolute value  
   delta = Math.abs(delta);  
  
   // If the difference is less than epsilon, then it's pretty close.  
   if (delta < epsilon)     
      return true;  
  
   return false;  
} // End of the floating-poing check function.  
  
// The triplet checker.   
function checkTriplet(a, b, c)  
{   
   // Create a temporary variable for swapping values  
   var d = 0;   
  
   // First, move the longest side to position "a".  
  
   // Swap a and b if necessary  
   if (b > a)  
   {  
      d = a;  
      a = b;  
      b = d;  
   }  
  
   // Swap a and c if necessary  
   if (c > a)  
   {  
      d = a;  
      a = c;  
      c = d;  
   }  
  
   // Test all 3 values. Are they integers?  
   if (((a % 1) == 0) && ((b % 1) == 0) && ((c % 1) == 0))  
   {   
      // If so, use the precise check.  
      return integerCheck(a, b, c);   
   }  
   else  
   {  
      // If not, get as close as is reasonably possible.  
      return floatCheck(a, b, c);   
   }  
} // End of the triplet check function.  
  
// The next three statements assign sample values for testing purposes.  
var sideA = 5;  
var sideB = 5;  
var sideC = Math.sqrt(50.001);  
  
// Call the function. After the call, 'result' contains the result.  
var result = checkTriplet(sideA, sideB, sideC);  
```  
  
<a name="Arrow"></a>   
## <a name="arrow-functions"></a>Функции со стрелкой  
 Синтаксис функции со стрелкой (`=>`) позволяет использовать сокращенное обозначение анонимной функции. Вот как это выглядит.  
  
```JavaScript  
([arg] [, arg]) => {  
    statements  
}  
```  
  
 Значения слева от стрелки, которые могут быть заключены в круглые скобки, определяют передаваемые в функцию аргументы. Для одного аргумента скобки не требуются. Если аргументы не передаются, необходимо использовать круглые скобки. Определение функции справа от стрелки может быть либо выражением (например, `v + 1`), либо блоком операторов, заключенным в фигурные скобки ({}).  
  
> [!IMPORTANT]
>  Синтаксис функции со стрелкой поддерживается только в [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 Функция со стрелкой не позволяет использовать оператор `new`.  
  
 В следующих примерах кода показано использование функции со стрелкой, определением которой служит выражение. В первом примере в качестве аргумента в выражение передается v. Во втором примере в качестве аргументов в выражение передаются v и i.  
  
```  
var evens = [2, 4, 6, 8];  
  
// Using standard syntax.  
var odds = evens.map(function(v) { return v + 1; });  
  
// Using arrow function syntax.  
// Add one to each value to produce output.  
var odds = evens.map(v => v + 1);  
  
// The following line of code adds the index value to the passed  
// in value to produce output.  
// Note: the second argument to the callback function in the map   
// method is the index value (i).  
var nums = evens.map((v, i) => v + i);  
  
console.log(odds);  
console.log(nums);  
  
// Output:  
// [object Array] [3, 5, 7, 9]  
// [object Array] [2, 5, 8, 11]  
```  
  
 В следующем примере кода показано использование функции со стрелкой, содержащей блок операторов.  
  
```JavaScript  
var fives = new Array();  
  
// Statement block, re-using nums array from previous example.  
// Note: The first argument to the callback function in forEach  
// is the value of the array element (v).  
nums.forEach(v => {  
  if (v % 5 === 0)  
    fives.push(v);  
});  
  
console.log(fives);  
  
// Output:  
// [object Array] [5]  
```  
  
 В отличие от стандартных функций, функции со стрелкой разделяют лексический объект `this` с окружающим их кодом, что позволяет не прибегать к таким решениям как `var self = this;`.  
  
 Следующий пример показывает, что объект `this` внутри функции со стрелкой имеет такое же значение, что и в окружающем эту функцию коде (который по-прежнему ссылается на переменную `bob`).  
  
```JavaScript  
var bob = {  
  _name: "Bob",  
  _friends: ["Pete", "Joe", "Larry"],  
  printFriends() {  
    this._friends.forEach(f =>  
      console.log(this._name + " knows " + f));  
  }  
}  
  
// Output:  
// Bob knows Pete  
// Bob knows Joe  
// Bob knows Larry  
```  
  
 Кроме того, функции со стрелкой разделяют с окружающим кодом лексический объект `arguments` (таким же образом, как и объект `this`).  
  
<a name="Default"></a>   
## <a name="default-parameters"></a>Параметры по умолчанию  
 Чтобы указать значение по умолчанию для параметра в функции, присвойте ему начальное значение. В качестве значения по умолчанию можно использовать константу или выражение.  
  
> [!IMPORTANT]
>  Параметры по умолчанию поддерживаются только в [!INCLUDE[jsv12textExp](../javascript/includes/jsv12textexp-md.md)].  
  
 В следующем примере значение Y по умолчанию равно 10, а значение Z по умолчанию — 20. Если вызывающая функция не передаст другое (или неопределенное) значение в виде второго аргумента, будет использоваться значение Y, равное 10. Если вызывающая функция не передаст другое (или неопределенное) значение в виде третьего аргумента, будет использоваться значение Z, равное 20.  
  
```JavaScript  
var val = 20;  
  
function f(x, y=10, z=val) {  
  return x + y + z;  
}  
  
console.log(f(3));  
console.log(f(3, 3));  
console.log(f(3, 3, 3));  
  
// Output:  
// 33  
// 26  
// 9  
```  
  
<a name="Rest"></a>   
## <a name="rest-parameters"></a>Параметры Rest  
 Параметры Rest, заданные оператором spread (), позволяют преобразовать последовательные аргументы в вызове функции в массив.  
  
 Параметры rest позволяют не использовать объект `arguments`. Между параметрами rest и объектом `arguments` существуют следующие различия:  
  
-   Параметр rest является экземпляром массива и поддерживает операции, которые могут выполняться с массивами.  
  
-   Параметр rest включает только последовательность аргументов, которые отдельно (в виде именованных аргументов) не передаются, а объект `arguments` содержит все передаваемые в функцию аргументы.  
  
> [!IMPORTANT]
>  Параметры rest и оператор spread поддерживаются только в [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 В следующем примере кода hello и true передаются как значения массива и сохраняются в параметр Y. Параметр rest должен быть последним параметром функции.  
  
```JavaScript  
function f(x, ...y) {  
  // y is an array.  
  return x * y.length;  
}  
  
console.log(f(3, "hello", true));  
  
// Output:  
// 6  
  
```  
  
 См. также статью [Оператор spread](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку JavaScript](../javascript/javascript-language-reference.md)