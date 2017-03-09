---
title: "Член &quot;&lt;имя_члена1&gt;&quot; неявно объявляет &quot;&lt;имя_неявного_члена&gt;&quot;, который конфликтует с членом, неявно объявленным для члена &quot;&lt;имя_члена2&gt;&quot; в базовом классе &quot;&lt;имя_базового_класса&gt;&quot; | Microsoft Docs"
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
  - "vbc40018"
  - "bc40018"
helpviewer_keywords: 
  - "BC40018"
ms.assetid: 43844e55-9ce1-4b88-9aa8-839b37f30e5a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Член &quot;&lt;имя_члена1&gt;&quot; неявно объявляет &quot;&lt;имя_неявного_члена&gt;&quot;, который конфликтует с членом, неявно объявленным для члена &quot;&lt;имя_члена2&gt;&quot; в базовом классе &quot;&lt;имя_базового_класса&gt;&quot;
Член "\<имя\_члена1\>" неявно объявляет "\<имя\_неявного\_члена\>", который конфликтует с членом, неявно объявленным для члена "\<имя\_члена2\>" в базовом классе "\<имя\_базового\_класса\>". Поэтому член должен объявляться как "Shadows".  
  
 Член производного класса создает неявный член с тем же именем, что и неявный член базового класса. Так как неявные члены не задают модификатор [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads), компилятор предполагает, что этот член [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) неявный член базового класса. Код становится более читаемым, и меньше вероятность возникновения ошибки, если для этого члена явно указать ключевое слово `Shadows`.  
  
 Компилятор [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] создает неявные члены, соответствующие определенным программным элементам, которые вы объявляете. В приведенной ниже таблице представлена сводка этих неявных или *искусственных* членов.  
  
|Объявленный элемент|Неявно созданные члены|  
|-------------------------|----------------------------|  
|Перечисление|Член `value__`|  
|Событие|Процедура `add_<eventname>`<br /><br /> Процедура `remove_<eventname>`<br /><br /> Поле `<eventname>Event`<br /><br /> Делегат `<eventname>EventHandler`|  
|Свойство|Процедура `get_<propertyname>`<br /><br /> Процедура `set_<propertyname>`|  
|Член `My.Form`, член `My.WebService` или член класса, помеченный атрибутом <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute>|Переменная `m_<variablename>` `Static`<br /><br /> Свойство `<variablename>`<br /><br /> Процедура `get_<variablename>`<br /><br /> Процедура `set_<variablename>`|  
|Переменная `WithEvents`|Переменная `_<variablename>`<br /><br /> Свойство `<variablename>`<br /><br /> Процедура `get_<variablename>`<br /><br /> Процедура `set_<variablename>`|  
  
 Из\-за риска конфликта имен следует избегать именования объявленных программных элементов с использованием той же формы, что и для этих неявных членов. Например, следует избегать использования имен элементов, начинающихся с `get_` или `set_`.  
  
 По умолчанию данное сообщение является предупреждением. Дополнительные сведения о скрытии предупреждений и обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40018  
  
### Исправление ошибки  
  
-   Если требуется скрыть или затемнить неявный член базового класса, включите ключевое слово [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) в объявление члена производного класса.  
  
-   Если не требуется затемнять неявный член базового класса, измените имя члена производного класса, чтобы избежать конфликтов с именами, перечисленными в предыдущей таблице.  
  
## См. также  
 [Имена объявленных элементов](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)