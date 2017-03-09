---
title: "Unknown argument for &#39;:&#39; operator. Complete Regular Expression required in search string. | Microsoft Docs"
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
  - "vs.message.0x800A00BE"
  - "vs.message.VS_E_RE_SPECIALUNKNOWN"
ms.assetid: 8cbc2f7f-7ea1-4803-904c-1f716cd36376
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unknown argument for &#39;:&#39; operator. Complete Regular Expression required in search string.
Эта ошибка обычно возникает при поиске или замене, если в строке поиска используются регулярные выражения или подстановочные знаки.  Был введен оператор\-двоеточие \(`:`\), но следующий за оператором аргумент не является допустимым аргументом.  
  
> [!NOTE]
>  Аргументы оператора\-двоеточия \(`:`\) вводятся с учетом регистра.  
  
### Чтобы исправить эту ошибку  
  
1.  Проверьте правильный синтаксис регулярных выражений, описанный в разделе "Регулярные выражения".  
  
2.  Еще раз проверьте правильность регистра используемого аргумента.  
  
3.  При использовании редактора метода ввода \(IME\) убедитесь, что аргумент задан без использования полноширинных знаков.  
  
## См. также  
 [Использование регулярных выражений в Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/ru-ru/dad03582-4931-4893-83ba-84b37f5b1600)   
 [Поиск в файлах](../ide/find-in-files.md)