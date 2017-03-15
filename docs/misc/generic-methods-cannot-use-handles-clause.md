---
title: "Универсальные методы не могут использовать предложение Handles | Microsoft Docs"
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
  - "vbc32080"
  - "BC32080"
helpviewer_keywords: 
  - "BC32080"
ms.assetid: 88c62a1c-aee3-46b2-ad78-76790022c04c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Универсальные методы не могут использовать предложение Handles
В объявлении универсальной процедуры `Sub` содержится предложение [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause).  
  
 Предложение `Handles` указывает список событий, которые обрабатывает процедура `Sub`. Чтобы быть обработчиком событий, процедура `Sub` должна иметь такую же сигнатуру, что и каждое событие, которое она может обрабатывать. Универсальную процедуру можно создать несколько раз, с сигнатурами, которые [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не может предсказать во время компиляции. Таким образом, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не может гарантировать сигнатуру, которая соответствует сигнатурам событий в предложении `Handles`.  
  
 **Идентификатор ошибки:** BC32080  
  
### Исправление ошибки  
  
-   Если процедура `Sub` должна быть универсальной, удалите предложение `Handles` из ее объявления. Используйте [Оператор AddHandler](/dotnet/visual-basic/language-reference/statements/addhandler-statement) для связывания этого обработчика событий с событием.  
  
-   Если процедура `Sub` должна использовать предложение `Handles` для связывания событий, удалите предложение [Of](/dotnet/visual-basic/language-reference/statements/of-clause) из ее объявления. Вы должны использовать неуниверсальную процедуру с предложением `Handles`.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [НЕ В СБОРКЕ. События и обработчики событий](http://msdn.microsoft.com/ru-ru/95074a0d-1cbc-4221-a95a-964185c7f962)