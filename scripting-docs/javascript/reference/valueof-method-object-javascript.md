---
title: "Метод valueOf (Object) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "valueOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "valueOf - метод"
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Метод valueOf (Object) (JavaScript)
Возвращает примитивное значение указанного объекта.  
  
## Синтаксис  
  
```  
  
object.valueOf( )  
```  
  
## Заметки  
 Обязательная ссылка `object` — это любой встроенный объект [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 Метод `valueOf` определяется по\-разному для каждого встроенного объекта [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
|Объект|Возвращаемое значение|  
|------------|---------------------------|  
|Array|Возвращает экземпляр массива.|  
|Boolean|Логическое значение.|  
|Date|Сохраненное значение времени, прошедшего после полуночи 1 января 1970 года \(UTC\) в миллисекундах.|  
|Функция|Сама функция.|  
|Number|Числовое значение.|  
|Объект|Сам объект.  Задано по умолчанию.|  
|Строка|Строковое значение.|  
  
 У объектов **Math** и `Error` метод `valueOf` отсутствует.  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **Относится к**: [Объект Array](../../javascript/reference/array-object-javascript.md)&#124; [Объект Boolean](../../javascript/reference/boolean-object-javascript.md)&#124; [Объект Date](../../javascript/reference/date-object-javascript.md)&#124; [Объект Function](../../javascript/reference/function-object-javascript.md)&#124; [Объект Number](../../javascript/reference/number-object-javascript.md)&#124; [Объект Object](../../javascript/reference/object-object-javascript.md)&#124; [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Метод toString \(Object\)](../../javascript/reference/tostring-method-object-javascript.md)