---
title: "Используйте параметр командной строки &quot;&lt;параметр&gt;&quot; или соответствующие параметры проекта вместо параметра &quot;&lt;параметр&gt;&quot; | Microsoft Docs"
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
  - "bc41008"
  - "vbc41008"
helpviewer_keywords: 
  - "BC41008"
ms.assetid: 1c5d6d7a-b767-4dae-aa61-d7fa81d5aad1
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Используйте параметр командной строки &quot;&lt;параметр&gt;&quot; или соответствующие параметры проекта вместо параметра &quot;&lt;параметр&gt;&quot;
Предпочтительный способ указания файла, содержащего открытый ключ для сборки, контейнер с открытым ключом для сборки или частично подписанную сборку, заключается в использовании параметров компилятора [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Не рекомендуется использовать в коде атрибуты <xref:System.Reflection.AssemblyKeyFileAttribute>, <xref:System.Reflection.AssemblyKeyNameAttribute> или <xref:System.Reflection.AssemblyDelaySignAttribute>.  
  
 **Идентификатор ошибки:** BC41008  
  
### Исправление ошибки  
  
1.  Используйте в своем коде параметры компилятора [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile), [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) или [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] вместо атрибутов <xref:System.Reflection.AssemblyKeyFileAttribute>, <xref:System.Reflection.AssemblyKeyNameAttribute> или <xref:System.Reflection.AssemblyDelaySignAttribute>.  
  
## См. также  
 [Практическое руководство. Создание подписанных дружественных сборок](../Topic/How%20to:%20Create%20Signed%20Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [Компилятор Visual Basic с интерфейсом командной строки](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile)   
 [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer)   
 [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign)