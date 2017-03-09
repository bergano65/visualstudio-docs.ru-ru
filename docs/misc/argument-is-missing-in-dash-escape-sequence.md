---
title: "Argument is missing in &#39;\&#39; escape sequence. | Microsoft Docs"
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
  - "vs.message.VS_E_RE_ESCAPEMISSINGARG"
  - "vs.message.0x800A00BD"
ms.assetid: 5bd6559b-8cd9-450f-91c8-335ff1b1ef86
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Argument is missing in &#39;\&#39; escape sequence.
Эта ошибка обычно возникает при поиске или замене, если в строке поиска используются регулярные выражения или подстановочные знаки.  Эта ошибка может быть вызвана одиночной обратной косой чертой \(`\`\) в конце шаблона либо `\x` или `\u`, введенными без правильного шестнадцатеричного символа Юникода.  
  
### Чтобы исправить эту ошибку  
  
1.  Чтобы выполнить поиск с помощью escape\-символа регулярного выражения, введите `\`.  
  
2.  Чтобы выполнить поиск символа Юникода, введите `\x` или `\u`, за которым следует допустимое значение Юникода.  
  
3.  Чтобы найти символ обратной косой черты, используйте `\\`.  
  
## См. также  
 [Использование регулярных выражений в Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/ru-ru/dad03582-4931-4893-83ba-84b37f5b1600)   
 [Поиск в файлах](../ide/find-in-files.md)