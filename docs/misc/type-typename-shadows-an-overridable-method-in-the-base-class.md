---
title: "&lt;тип&gt; &quot;&lt;имя_типа&gt;&quot; затемняет переопределяемый метод в базовом классе | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40005"
  - "bc40005"
helpviewer_keywords: 
  - "BC40005"
ms.assetid: 1dadda7f-1d26-4ae8-a668-9f69d55ceb50
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;тип&gt; &quot;&lt;имя_типа&gt;&quot; затемняет переопределяемый метод в базовом классе
\<тип\> "\<имя\_типа\>" затемняет переопределяемый метод в базовом классе. Если требуется переопределение метода базового класса, этот метод должен объявляться как "Overrides".  
  
 Программный элемент объявлен с тем же именем, что и переопределяемая процедура или свойство, определенное в базовом классе. В этом случае элемент в данном классе должен затемнять элемент базового класса.  
  
 По умолчанию данное сообщение является предупреждением. Дополнительные сведения о скрытии предупреждений и обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40005  
  
### Исправление ошибки  
  
-   Если вы собираетесь переопределять базовую процедуру, добавьте в объявление ключевое слово `Overrides`.  
  
-   Если вы собираетесь затемнять базовую процедуру, добавьте в объявление ключевое слово `Shadows`.  
  
-   Если ни переопределение, ни затемнение не планируются, измените имя объявляемого элемента.  
  
## См. также  
 [НЕ В СБОРКЕ. Переопределение свойств и методов](http://msdn.microsoft.com/ru-ru/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Сокрытие в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)