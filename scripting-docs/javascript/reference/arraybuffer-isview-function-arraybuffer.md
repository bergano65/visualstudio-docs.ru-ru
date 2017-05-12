---
title: "Функция ArrayBuffer.isView (ArrayBuffer) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Функция ArrayBuffer.isView (ArrayBuffer)
Определяет, обеспечивает ли объект представление буфера.  
  
## Синтаксис  
  
```javascript  
ArrayBuffer.isView(object)  
```  
  
#### Параметры  
 `object`  
 Обязательный.  Объект для тестирования.  
  
## Возвращаемое значение  
 `true`, если справедливо одно из следующих условий:  
  
-   `object` является объектом `DataView`.  
  
-   `object` является типизированным массивом.  
  
 В противном случае метод возвращает значение `false`.  
  
## Заметки  
  
## Пример  
 В следующем примере показано использование функции `isView` для тестирования типизированного массива и объекта `DataView`.  
  
```javascript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## Требования  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## См. также  
 [Объект Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)