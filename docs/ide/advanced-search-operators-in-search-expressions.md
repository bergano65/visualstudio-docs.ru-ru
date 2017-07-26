---
title: "Операторы расширенного поиска в выражениях поиска | Microsoft Docs"
ms.custom: 
ms.date: 06/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 07ff2413503209d6ade252ac89dbfbe2589e7e85
ms.openlocfilehash: 7ad9c78134c337445a3e9180ad27234b7bcb07cc
ms.contentlocale: ru-ru
ms.lasthandoff: 06/02/2017

---
# <a name="advanced-search-operators-in-search-expressions"></a>Операторы расширенного поиска в выражениях поиска
С помощью расширенных операторов поиска в окне справки можно уточнить поиск содержимого путем создания более сложных выражений на основе простых. Как показано в следующей таблице, эти операторы ограничивают контекст, в котором выполняется запрос.  

> [!WARNING]
>  Операторы расширенного поиска вводятся с двоеточием на конце и без промежуточных пробелов перед двоеточием: только так поисковая система сможет распознать их.  

|Условие, которое требуется найти|Применение|Пример|Результат|  
|-------------------|---------|-------------|------------|  
|Термин в заголовке раздела|title:|title:binaryreader|Разделы, содержащие "binaryreader" в заголовках.|  
|Термин в примере кода|code:|code:readdouble|Разделы, содержащие"readdouble" в примере кода.|  
|Термин в примере конкретного языка программирования|code:vb:|code:vb:string|Разделы, содержащие "string", в примере Visual Basic.|  
|Раздел, связанный с конкретным ключевым словом индекса|keyword:|keyword:readbyte|Разделы, связанные с ключевым словом индекса "readbyte"|  

 Оператор code: можно использовать для поиска сведений о любом из нескольких языков программирования, но он возвращает результаты только для содержимого, которое включает отметку о конкретном языке программирования. В следующей таблице перечислены языки программирования, которые поддерживает этот оператор.  

|Язык программирования|Применение|  
|--------------------------|---------|  
|Visual Basic|code:vb<br /><br /> или<br /><br /> code:visualbasic|  
|C#|code:c#<br /><br /> или<br /><br /> code:csharp|  
|C++|code:cpp<br /><br /> или<br /><br /> code:c++<br /><br /> или<br /><br /> code:cplusplus|  
|F#|code:f#<br /><br /> или<br /><br /> code:fsharp|  
|JavaScript|code:javascript<br /><br /> или<br /><br /> code:js|  
|XAML|code:xaml|  

## <a name="see-also"></a>См. также  
 [Логические операторы в выражениях поиска](../ide/logical-operators-in-search-expressions.md)   
 [Советы по полнотекстовому поиску](../ide/full-text-search-tips.md)

