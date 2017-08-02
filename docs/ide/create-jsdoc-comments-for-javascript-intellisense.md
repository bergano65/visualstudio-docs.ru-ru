---
title: "Создание комментариев JSDoc для JavaScript IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Создание комментариев JSDoc для JavaScript IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Технология IntelliSense в Visual Studio отображает сведения, которые добавляются в скрипт с помощью стандартных комментариев JSDoc.  Комментарии JSDoc можно использовать для предоставления сведений об элементах кода, например о функциях, полях и переменных.  
  
## Теги для комментариев JSDoc  
 В технологии IntelliSense для отображения сведений о коде используются следующие стандартные теги для комментариев JSDoc.  
  
|Тег JSDoc|Синтаксис|Примечания|  
|---------------|---------------|----------------|  
|@deprecated|@deprecated *описание*|Указывает устаревшую функцию или метод.|  
|@description|@description *описание*|Указывает описание для функции или метода.|  
|@param|@param {*тип*} *parameterName**описание*|Указывает сведения для параметра в функции или методе.<br /><br /> TypeScript также поддерживает @paramTag.|  
|@property|@property {*тип*} *propertyName*|Указывает сведения, включая описание, для поля или элемента, который определен в объекте.|  
|@returns|@returns {*тип*}|Указывает возвращаемое значение.<br /><br /> Для TypeScript используйте @returnType вместо @returns.|  
|@summary|@summary *описание*|Указывает описание для функции или метода \(аналогично @description\).|  
|@type|@type {*тип*}|Указывает тип для константы или переменной.|  
|@typedef|@typedef {*тип*} *customTypeName*|Указывает пользовательский тип.|  
  
### Примеры  
 В следующем примере показано использование тегов JSDoc @description, @param и @return для функции с именем `getArea`.  
  
```javascript  
/** @description Determines the area of a circle that has the specified radius parameter.  
 * @param {number} radius The radius of the circle.  
 * @return {number}  
 */  
function getArea(radius) {  
    var areaVal;  
    areaVal = Math.PI * radius * radius;  
    return areaVal;  
}  
```  
  
 В предыдущем примере IntelliSense отображает описание, параметры и возвращаемые сведения при вводе открывающей скобки для `getArea`.  
  
 ![Сведения IntelliSense для функции](~/ide/media/js_intellisense_jsdoc_comments.png "JS\_IntelliSense\_JSDoc\_Comments")  
  
 В примере показано, как использовать тег @typedef с тегом @property.  
  
```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  
  
var w = new Weather();  
```  
  
 В следующем примере показано использование тегов JSDoc @type.  Как показано в этом примере, одиночные звездочки \(\*\), которые следуют за начальными двойными звездочками \(\*\*\), не являются обязательными.  
  
```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  
  
```  
  
 В следующем примере показано, как использовать тег JSDoc @deprecated.  
  
```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```