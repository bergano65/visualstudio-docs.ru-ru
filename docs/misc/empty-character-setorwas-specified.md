---
title: "Указан пустой символ setorwas. | Microsoft Docs"
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
  - "vs.message.VS_E_RE_EMPTYSET"
  - "vs.message.0x800A00DF"
ms.assetid: 27ed2ebe-a492-4bc9-ab33-a09fba6cf1d3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Указан пустой символ setorwas.
Эта ошибка обычно возникает, если выбран параметр регулярных выражений и для шаблонов **Набор знаков \[\]** или **Знак не из набора \[^\]** указана строка, содержащая неполный синтаксис.  Например, `[}`.  
  
### Чтобы исправить эту ошибку  
  
1.  Просмотрите сведения о правильном синтаксисе для шаблона в разделе "Регулярные выражения" и введите строку повторно.  
  
## См. также  
 [Использование регулярных выражений в Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/ru-ru/dad03582-4931-4893-83ba-84b37f5b1600)   
 [Поиск в файлах](../ide/find-in-files.md)   
 [Поиск и замена текста](../ide/finding-and-replacing-text.md)