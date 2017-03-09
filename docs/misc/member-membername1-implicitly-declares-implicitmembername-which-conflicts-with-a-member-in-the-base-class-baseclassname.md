---
title: "Член &quot;&lt;имя_члена1&gt;&quot; неявно объявляет &quot;&lt;имя_неявного_члена&gt;&quot;, который конфликтует с членом в базовом классе &quot;&lt;имя_базового класса&gt;&quot;. | Microsoft Docs"
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
  - "vbc40022"
  - "bc40022"
helpviewer_keywords: 
  - "BC40022"
ms.assetid: be5bb2ee-2274-42b2-b843-179b14127b34
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Член &quot;&lt;имя_члена1&gt;&quot; неявно объявляет &quot;&lt;имя_неявного_члена&gt;&quot;, который конфликтует с членом в базовом классе &quot;&lt;имя_базового класса&gt;&quot;.
Член "\<имя\_члена1\>" неявно объявляет "\<имя\_неявного\_члена\>", который конфликтует с членом в базовом классе "\<имя\_базового класса\>", и поэтому этот член не должен объявляться как Overloads.  
  
 Свойство в производном классе создает неявный член с тем же именем, что и у члена базового класса, и задает ключевое слово [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads).  
  
 Перегрузка используется для задания нескольких версий свойства или процедуры в одном и том же классе. Нельзя определить дополнительную версию члена базового класса, если он не задает `Overloads`. Так как конфликтующий член базового класса не задает `Overloads`, компилятор предполагает, что это свойство [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) неявный член базового класса.  
  
 Компилятор [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] создает неявные члены, соответствующие определенным программным элементам, которые вы объявляете. В приведенной ниже таблице представлена сводка этих неявных или *искусственных* членов.  
  
|Объявленный элемент|Неявно созданные члены|  
|-------------------------|----------------------------|  
|Перечисление|Член `value__`|  
|Событие|Процедура `add_<eventname>`<br /><br /> Процедура `remove_<eventname>`<br /><br /> Поле `<eventname>Event`<br /><br /> Делегат `<eventname>EventHandler`|  
|Свойство|Процедура `get_<propertyname>`<br /><br /> Процедура `set_<propertyname>`|  
|Член `My.Form`, член `My.WebService` или член класса, помеченный атрибутом <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute>|Переменная `m_<variablename>` `Static`<br /><br /> Свойство `<variablename>`<br /><br /> Процедура `get_<variablename>`<br /><br /> Процедура `set_<variablename>`|  
|Переменная `WithEvents`|Переменная `_<variablename>`<br /><br /> Свойство `<variablename>`<br /><br /> Процедура `get_<variablename>`<br /><br /> Процедура `set_<variablename>`|  
  
 Из\-за риска конфликта имен следует избегать именования объявленных программных элементов с использованием той же формы, что и для этих неявных членов. Например, следует избегать использования имен элементов, начинающихся с `get_` или `set_`.  
  
 По умолчанию данное сообщение является предупреждением. Дополнительные сведения о сокрытии предупреждений и обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40022  
  
### Исправление ошибки  
  
-   Если требуется скрыть или затемнить член базового класса, замените ключевое слово [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) ключевым словом [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) в объявлении свойства.  
  
-   Если вы не собираетесь затемнять член базового класса, измените имя этого свойства, чтобы избежать конфликтов имен, перечисленных в предыдущей таблице.  
  
## См. также  
 [Имена объявленных элементов](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)