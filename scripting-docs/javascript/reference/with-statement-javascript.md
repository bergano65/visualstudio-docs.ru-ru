---
title: "Оператор with (JavaScript) | Microsoft Docs"
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
  - "with_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "With - оператор"
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Оператор with (JavaScript)
Устанавливает объект по умолчанию для оператора.  
  
## Синтаксис  
  
```  
with (object) {  
    statements  
}   
```  
  
## Параметры  
 `object`  
 Объект по умолчанию.  
  
 `statements`  
 Один или несколько операторов, для которых `object` является объектом по умолчанию.  
  
## Заметки  
 Для сокращения объема кода, который необходимо написать в некоторых случаях, обычно используется оператор `with`.  
  
> [!WARNING]
>  Использование `with` в строгом режиме не допускается.  Оператор `with` может усложнить чтение и отладку кода, поэтому обычно следует избегать его использования.  
  
## Пример  
 В следующем примере объект `Math` используется несколько раз.  
  
```javascript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## Пример  
 Если переписать этот пример с использованием оператора `with`, код будет короче.  
  
```javascript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор this](../../javascript/reference/this-statement-javascript.md)