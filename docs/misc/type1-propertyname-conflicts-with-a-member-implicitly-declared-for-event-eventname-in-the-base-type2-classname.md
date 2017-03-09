---
title: "&lt;тип1&gt; &quot;&lt;имя_свойства&gt;&quot; вступает в противоречие с членом, объявленным неявно в &lt;тип2&gt; &quot;&lt;имя_класса&gt;&quot; для события &quot;&lt;имя_события&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40014"
  - "bc40014"
helpviewer_keywords: 
  - "BC40014"
ms.assetid: 100534b9-d533-4e94-a2a7-0ed26426965b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;тип1&gt; &quot;&lt;имя_свойства&gt;&quot; вступает в противоречие с членом, объявленным неявно в &lt;тип2&gt; &quot;&lt;имя_класса&gt;&quot; для события &quot;&lt;имя_события&gt;&quot;
Свойство объявлено с тем же именем, что и неявный член, сформированный на основе события в базовом классе. Например, если базовый класс определяет событие с именем `Event1`, компилятор создает неявные процедуры `add_Event1` и `remove_Event1`. Если свойство в этом классе имеет одно из этих имен, оно должно затемнять член базового класса.  
  
 Это сообщение является предупреждением.`Shadows` подразумевается по умолчанию. Дополнительные сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40014  
  
### Исправление ошибки  
  
1.  Чтобы скрыть член базового класса, добавьте к объявлению свойства ключевое слово `Shadows`.  
  
2.  Если не требуется скрывать член базового класса, измените имя свойства.  
  
## См. также  
 [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Сокрытие в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)