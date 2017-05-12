---
title: "Непредвиденный квантификатор (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Непредвиденный квантификатор (JavaScript)
При составлении шаблона поиска регулярного выражения создан элемент шаблона с недопустимой кратностью.  Например, шаблон  
  
```  
/^+/  
```  
  
 недопустим, так как элемент ^ \(начало входных данных\) не может иметь кратность.  В следующей таблице перечислены элементы, которые не могут иметь кратность.  
  
|Элемент|Описание|  
|-------------|--------------|  
|^|Начало входных данных|  
|$|Конец входных данных|  
|\\b|Граница слова|  
|\\B|Не граница слова|  
|\*|Ноль или более повторений|  
|\+|Одно или более повторений|  
|?|Ноль или одно повторение|  
|{n}|n повторений|  
|{n,}|n или более повторений|  
|{n,m}|От n до m повторений, включительно|  
  
### Исправление ошибки  
  
-   Убедитесь, что элемент шаблона поиска содержит только допустимые кратности.  
  
## См. также  
 [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)