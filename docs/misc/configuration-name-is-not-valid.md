---
title: "Configuration name is not valid. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INVALID_CFG_NAME"
  - "vs.message.0x800A00B7"
ms.assetid: aa439582-0863-41d3-825c-7c45b1773cde
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Configuration name is not valid.
Эта ошибка обычно возникает, если имя, введенное для конфигурации построения, содержит недопустимые знаки, такие как "\<", "\>", "&#124;" и "\*".  
  
### Чтобы исправить эту ошибку  
  
1.  Проверьте, что имя конфигурации не содержит следующих знаков: "\<", "\>", "\*", "&#124;", ":", "\\", "\/", "&", "%", """,« .", "\#", "?" и начальный и конечный пробелы.  Кроме того, имя конфигурации не может быть именем, зарезервированным для Windows или DOS, например "nul", "aux", "con', "com\#", "lpt\#" и т. д.  
  
2.  Еще раз введите имя.  
  
## См. также  
 [Построение приложений в Visual Studio](../ide/compiling-and-building-in-visual-studio.md)