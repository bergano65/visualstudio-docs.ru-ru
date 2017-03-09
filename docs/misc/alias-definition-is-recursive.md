---
title: "Alias definition is recursive. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A00DA"
  - "vs.message.VS_E_RECURSIVEALIAS"
ms.assetid: e48a2908-9b94-4c6a-9807-beeeba71531c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Alias definition is recursive.
Эта ошибка обычно возникает, если был определен псевдоним, который прямо или косвенно ссылается сам на себя.  
  
### Чтобы исправить эту ошибку  
  
1.  Измените определение псевдонима и повторите попытку.  
  
     —или—  
  
2.  Просмотрите текущий список псевдонимов и их определения, введя `>alias` в окне **Команда**, и повторите попытку.  
  
## См. также  
 [Команда Alias](../ide/reference/alias-command.md)   
 [Псевдонимы команд Visual Studio](../ide/reference/visual-studio-command-aliases.md)