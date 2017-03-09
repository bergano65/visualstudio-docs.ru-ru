---
title: "Метод &lt;тип&gt; &quot;&lt;имя_метода&gt;&quot; конфликтует с другими членами того же имени в иерархии наследования, и поэтому должен быть объявлен как Shadows | Microsoft Docs"
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
  - "vbc42000"
  - "bc42000"
helpviewer_keywords: 
  - "BC42000"
ms.assetid: 3081635f-99a9-4e90-997f-82251144d80f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод &lt;тип&gt; &quot;&lt;имя_метода&gt;&quot; конфликтует с другими членами того же имени в иерархии наследования, и поэтому должен быть объявлен как Shadows
Интерфейс, наследуемый от нескольких интерфейсов, определяет процедуру с тем же именем, что и процедура, уже определенная в нескольких базовых интерфейсах. Процедура в этом интерфейсе должна затемнять одну из процедур базового интерфейса.  
  
 Это сообщение является предупреждением.`Shadows` подразумевается по умолчанию. Дополнительные сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42000  
  
### Исправление ошибки  
  
-   Если требуется скрыть одну из процедур базового интерфейса, добавьте ключевое слово `Shadows` в объявление новой процедуры.  
  
-   Если не требуется скрывать какую\-либо процедуру базового интерфейса, измените имя новой процедуры.  
  
## См. также  
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Сокрытие в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)