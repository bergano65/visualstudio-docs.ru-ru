---
title: "Область действия переменной (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "область действия, JavaScript"
  - "область действия переменной [JavaScript]"
  - "переменные, область действия [JavaScript]"
ms.assetid: a811a9a6-856f-46e9-8be3-f2d22a0c245f
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Область действия переменной (JavaScript)
В языке [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] имеется две области действия: глобальная и локальная.  Переменная, объявляемая вне определения функции, является глобальной, и ее значение доступно и может быть изменено в любом месте программы.  Переменная, объявляемая внутри определения функции, является локальной.  Она создается и уничтожается при каждом выполнении функции и не доступна никакому коду за пределами данной функции.  JavaScript не поддерживает область видимости блока \(в которой пара фигурных скобок `{. . .}` определяет новую область\), за исключением особого случая наличия переменных, видимых в пределах блока.  
  
## Область в JavaScript  
 Локальная переменная может иметь такое же имя, как глобальная, но это совершенно разные переменные; изменение значения одной переменной не влияет на значение другой.  Внутри функции, где объявлена локальная переменная, имеет значение только эта локальная версия.  
  
```javascript  
// Global definition of aCentaur.  
var aCentaur = "a horse with rider,";  
  
// A local aCentaur variable is declared in this function.  
function antiquities(){  
  
   var aCentaur = "A centaur is probably a mounted Scythian warrior";  
}  
  
antiquities();  
aCentaur += " as seen from a distance by a naive innocent.";  
  
document.write(aCentaur);  
  
// Output: "a horse with rider, as seen from a distance by a naive innocent."  
```  
  
 В JavaScript переменные вычисляются так, как если бы они были объявлены в начале той области, в которой находятся.  Иногда это может приводить к непредвиденному поведению, как показано ниже.  
  
```javascript  
var aNumber = 100;  
tweak();  
  
function tweak(){  
  
    // This prints "undefined", because aNumber is also defined locally below.  
    document.write(aNumber);  
  
    if (false)  
    {  
        var aNumber = 123;    
    }  
}  
```  
  
 Когда программа [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняет какую\-либо функцию, сначала она находит все объявления переменных, например `var someVariable;`.  Она создает переменные с начальным значением `undefined`.  Если переменная объявлена с некоторым значением, например `var someVariable = "something";`, она все равно изначально создается со значением `undefined`, а объявленное значение принимает только при выполнении строки, содержащей это объявление.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обрабатывает все объявления переменных до выполнения любого кода независимо от того, находится ли объявление внутри условного блока или другой конструкции.  После того [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] обнаруживает все переменные, начинается выполнение кода функции.  Если переменная неявно объявлена внутри функции \(т. е. находится в левой части выражения присваивания, но объявлена без ключевого слова `var`\), она является глобальной.  
  
 В JavaScript внутренняя \(вложенная\) функция сохраняет ссылки на локальные переменные, присутствующие в той же области, что и она сама, даже после того как эта функция возвращает результат.  Такой набор ссылок называется замкнутым выражением.  В следующем примере второй вызов внутренней функции выводит то же сообщение \("Hello Bill"\), что и первый, так как входной параметр для внешней функции `name` является локальной переменной, находящейся в замкнутом выражении для внутренней функции.  
  
```javascript  
function send(name) {  
    // Local variable 'name' is stored in the closure  
    // for the inner function.  
    return function () {  
        sendHi(name);  
    }  
}  
  
function sendHi(msg) {  
    console.log('Hello ' + msg);  
}  
  
var func = send('Bill');  
func();  
// Output:  
// Hello Bill  
sendHi('Pete');  
// Output:  
// Hello Pete  
func();  
// Output:  
// Hello Bill  
```  
  
## Переменные, видимые в пределах блока  
 В Internet Explorer 11 предусмотрена поддержка переменных [let](../../javascript/reference/let-statement-javascript.md) и [const](../../javascript/reference/const-statement-javascript.md), видимых в пределах блока.  Для этих переменных фигурные скобки `{. . .}` определяют новую область.  При присвоении одной из этих переменных конкретного значения это значение применяется только для области, в которой оно задано.  
  
 В следующем примере показано использование переменной `let` и блоковой области.  
  
> [!NOTE]
>  Приведенный ниже код поддерживается в стандартном режиме Internet Explorer версии 11 и более поздних версий.  
  
```javascript  
let x = 10;  
var y = 10;  
{  
    let x = 5;  
    var y = 5;  
    {  
        let x = 2;  
        var y = 2;  
        document.write("x: " + x + "<br/>");  
        document.write("y: " + y + "<br/>");  
        // Output:  
        // x: 2  
        // y: 2  
    }  
    document.write("x: " + x + "<br/>");  
    document.write("y: " + y + "<br/>");  
    // Output:  
    // x: 5  
    // y: 2  
}  
  
document.write("x: " + x + "<br/>");  
document.write("y: " + y + "<br/>");  
// Output:  
// x: 10  
// y: 2  
```