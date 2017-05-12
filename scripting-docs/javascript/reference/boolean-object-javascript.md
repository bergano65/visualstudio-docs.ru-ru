---
title: "Объект Boolean (JavaScript) | Microsoft Docs"
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
  - "boolean_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "boolean - тип данных, Boolean - объект"
  - "Boolean - объект"
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Объект Boolean (JavaScript)
Создает новое логическое значение.  
  
## Синтаксис  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## Параметры  
 `boolObj`  
 Обязательный.  Имя переменной, которой присваивается объект `Boolean`.  
  
 `boolValue`  
 Необязательный.  Начальное значение типа Boolean для нового объекта.  Если аргумент `boolvalue` опущен, имеет значение `false`, 0, `null`, `NaN` или является пустой строкой, начальным значением объекта Boolean является `false`.  В противном случае начальным значением является значение `true`.  
  
## Заметки  
 Объект `Boolean` является оболочкой типа данных Boolean.  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] неявно использует объект `Boolean` при преобразовании логического типа данных Boolean в объект `Boolean`.  
  
 Явное создание объектов `Boolean` используется редко.  
  
## Свойства  
 В приведенной ниже таблице перечислены свойства объекта `Boolean`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Свойство constructor](../../javascript/reference/constructor-property-boolean.md)|Указывает функцию, которая создает объект типа Boolean.|  
|[Свойство prototype](../../javascript/reference/prototype-property-boolean.md)|Возвращает ссылку на прототип объекта Boolean.|  
  
<a name="js56jsobjarraymeth"></a>   
## Методы  
 В приведенной ниже таблице перечислены методы объекта `Boolean`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Метод toString](../../javascript/reference/tostring-method-boolean-1.md)|Возвращает строковое представление объекта Boolean.|  
|[Метод valueOf](../../javascript/reference/valueof-method-boolean.md)|Получает ссылку на объект Boolean.|  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]