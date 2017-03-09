---
title: "Член&quot;&lt;membername&gt;&quot; неявно определяет член &quot;&lt;implicitmembername&gt;&quot;, который содержит то же имя, что и у параметра типа | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC32070"
  - "vbc32070"
helpviewer_keywords: 
  - "BC32070"
ms.assetid: cc0b3fcf-c141-47e2-9b33-d2b91c8bf2d6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Член&quot;&lt;membername&gt;&quot; неявно определяет член &quot;&lt;implicitmembername&gt;&quot;, который содержит то же имя, что и у параметра типа
Член универсального типа создает неявный член с тем же именем, что и у параметра типа для класса.  
  
 Компилятор [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] создает неявные члены, соответствующие определенным программным элементам, которые вы объявляете. В следующей таблице представлена сводка этих неявных или *искусственных* членов.  
  
|Объявленный элемент|Неявно созданные члены|  
|-------------------------|----------------------------|  
|Перечисление|Член `value__`|  
|Событие|Процедура `add_<eventname>`<br /><br /> Процедура `remove_<eventname>`<br /><br /> Поле `<eventname>Event`<br /><br /> Делегат `<eventname>EventHandler`|  
|Свойство|Процедура `get_<propertyname>`<br /><br /> Процедура `set_<propertyname>`|  
|Переменная коллекции `My.`|Переменная `m_<variablename>` `Static`<br /><br /> Свойство `<variablename>`<br /><br /> Процедура `get_<variablename>`<br /><br /> Процедура `set_<variablename>`|  
|Переменная `WithEvents`|Переменная `_<variablename>`<br /><br /> Свойство `<variablename>`<br /><br /> Процедура `get_<variablename>`<br /><br /> Процедура `set_<variablename>`|  
  
 Из\-за возможных конфликтов имен следует избегать именования объявленного программного элемента с использованием той же формы, что и у любого из этих неявных членов. Например, следует избегать любого имени элемента, которое начинается с `get_` или `set_`.  
  
 **Идентификатор ошибки:** BC32070  
  
### Исправление ошибки  
  
-   Если имя параметра типа является гибким, измените его, чтобы избежать конфликтов с именами, перечисленными в предыдущей таблице.  
  
-   Если параметр типа должен сохранить свое имя, измените имя члена класса, чтобы избежать конфликтов с именами, перечисленными в предыдущей таблице.  
  
## См. также  
 [Имена объявленных элементов](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)