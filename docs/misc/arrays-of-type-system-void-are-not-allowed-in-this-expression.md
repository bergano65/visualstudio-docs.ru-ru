---
title: "Массивы типа System.Void недопустимы в данном выражении. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31428"
  - "bc31428"
helpviewer_keywords: 
  - "BC31428"
ms.assetid: 21d77b56-585f-4107-b7ec-21933ba58017
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Массивы типа System.Void недопустимы в данном выражении.
Выражение в операторе назначения или объявления задает массив типа <xref:System.Void>.  
  
 Структура <xref:System.Void> является специализированным типом, который используется внутренне платформой .NET Framework и особенно Visual C\# и Visual C\+\+. Она представляет тип возвращаемого значения для метода, который не возвращает значение. Visual Basic использует процедуру `Sub`, если значение не возвращается, и процедуру `Function`, если возвращается.  
  
 Массивы типа <xref:System.Void> не имеют смысла и не разрешены в любом контексте.  
  
 **Идентификатор ошибки:** BC31428  
  
### Исправление ошибки  
  
1.  Удалите круглые скобки, которые указывают массив.  
  
2.  Если нет конкретной причины для сравнения типа времени выполнения с <xref:System.Void>, удалите ссылку на него полностью.  
  
## См. также  
 <xref:System.Void>