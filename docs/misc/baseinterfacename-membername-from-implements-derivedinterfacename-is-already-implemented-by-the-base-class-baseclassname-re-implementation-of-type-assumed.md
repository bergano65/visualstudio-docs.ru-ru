---
title: "&quot;&lt;baseinterfacename&gt;.&lt;membername&gt;&quot; из &quot;implements &lt;derivedinterfacename&gt;&quot; уже реализован базовым классом &quot;&lt;baseclassname&gt;&quot;. Предполагается повторная реализация &lt;type&gt; | Microsoft Docs"
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
  - "bc42014"
  - "vbc42014"
helpviewer_keywords: 
  - "BC42014"
ms.assetid: 95fff622-5d54-4ec8-90f0-477de1d58687
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;baseinterfacename&gt;.&lt;membername&gt;&quot; из &quot;implements &lt;derivedinterfacename&gt;&quot; уже реализован базовым классом &quot;&lt;baseclassname&gt;&quot;. Предполагается повторная реализация &lt;type&gt;
Свойство, процедура или событие производного класса использует предложение `Implements`, указывая элемент производного интерфейса, который уже реализован для базового интерфейса в базовом классе.  
  
 Реализуемый элемент определяется базовым интерфейсом и наследуется производным интерфейсом. Базовый класс непосредственно реализует базовый интерфейс. Производный класс реализует производный интерфейс и может легко пропустить тот факт, что базовый класс уже реализовал этот элемент.  
  
 Производный класс может повторно реализовать элемент интерфейса, который реализован его базовым классом. Это не та же переопределяющая реализация базового класса. Для получения дополнительной информации см. [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause).  
  
 По умолчанию данное сообщение является предупреждением. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42014  
  
### Исправление ошибки  
  
-   Если вы собираетесь реализовать элемент интерфейса, вам не нужно предпринимать никаких действий. Код в производном классе получает доступ к повторно реализованному элементу, если вы не используете ключевое слово [MyBase \- delete](http://msdn.microsoft.com/ru-ru/52491d06-6451-4f6f-9aa6-8fab59bbc2b9) для доступа к базе данных реализации.  
  
-   Если вы не собираетесь реализовать элемент интерфейса, удалите предложение `Implements` из свойства, процедуры или объявления события.  
  
## См. также  
 [Интерфейсы](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [НЕ В СБОРКЕ. ключевое слово Implements и оператор Implements](http://msdn.microsoft.com/ru-ru/b96560f7-6413-480f-a1e2-f80253bab5be)