---
title: "Условные атрибуты схемы VSCT XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Элементы схемы VSCT XML, условные атрибуты"
  - "условные атрибуты (VSCT XML-схемы)"
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Условные атрибуты схемы VSCT XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Условные атрибуты можно применять все списки и элементы. Логические операторы и выражения расширения символ оценить значение true или false. Значение true, если связанный список или элемент включается в результат.  
  
 Можно протестировать маркера расширения от других маркеров расширения или константы. Функция Defined\(\) используется для проверки определенного имени определен, даже если он не имеет значения.  
  
 При применении атрибута к списку условие применяется для каждого дочернего элемента в списке. Если сам дочерний элемент содержит атрибут Condition, затем его условие в сочетании с родительское выражение операцией и.  
  
 Значения «true», «1» и 1 оцениваются как true, и 0, «0» и «false» вычисляются как false.  
  
## Операторы  
 Следующие операторы могут использоваться для оценки условных выражений.  
  
|Оператор|Определение|  
|--------------|-----------------|  
|\(,\)|Группирование|  
|\!|Логическое НЕ|  
|\<, \>, \<\=, \>\=, \=\=, \!\=|Реляционные операторы равенства и|  
|и|Boolean|  
|или|Boolean|  
  
## Примеры  
  
```  
<Menu Condition="Defined(DEBUG)" … </Menu> <Menu Condition="%(SKU_MODE) = 'Demo'" … </Menu> <Menus Condition="Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menus Condition="Defined(DEMO_SKU)"> <Menus Condition="!Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menu … </Menu> </Menus> <Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU)) and !Defined(DEBUG)"> <Menu … </Menu> </Menus>  
```  
  
## См. также  
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)