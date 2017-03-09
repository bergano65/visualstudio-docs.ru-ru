---
title: "Неиспользуемая локальная переменная: &quot;&lt;имя_локальной_переменной&gt;&quot; | Microsoft Docs"
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
  - "vbc42024"
  - "BC42024"
helpviewer_keywords: 
  - "BC42024"
ms.assetid: 749b1315-0f85-4f7e-b68b-8cc4346c502b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Неиспользуемая локальная переменная: &quot;&lt;имя_локальной_переменной&gt;&quot;
Локальная переменная в процедуре объявлена, но не используется.  
  
 Возможно, допущена ошибка в написании локальных переменных в процедуре. Если эта переменная используется в другом операторе, но отличается по написанию, то это будет воспринято компилятором как две различные переменные.  
  
 По умолчанию данное сообщение является предупреждением. Дополнительные сведения о скрытии предупреждений и обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42024  
  
### Исправление ошибки  
  
1.  Проверьте наличие орфографических ошибок в локальных переменных в процедуре. Обратите внимание на то, что регистр не учитывается. Считается, что имена `ABC` и `abc` указывают на одну и ту же переменную.  
  
2.  Если орфографических ошибок нет, то либо удалите объявление этой переменной, либо используйте ее в другом операторе в процедуре.  
  
## См. также  
 [Имена объявленных элементов](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)