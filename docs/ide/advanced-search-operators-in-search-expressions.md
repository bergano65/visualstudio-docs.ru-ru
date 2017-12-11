---
redirect_url: /visualstudio/ide/logical-operators-in-search-expressions
ms.openlocfilehash: fe896af873197c95a4b226396e0b6333fdc40cfa
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2017
---
title: "Операторы расширенного поиска в выражениях поиска | Документы Майкрософт" ms.custom: "" ms.date: "06/02/2017" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-help-viewer" ms.tgt_pltfrm: "" ms.topic: "article" helpviewer_keywords: 
  - "Окно справки, поиск по ключевым словам"
  - "Окно справки, поиск в коде"
  - "Окно справки, поиск в коде по языку программирования"
  - "Окно справки, поиск в заголовках"
  - "поиск в коде [окно справки]"
  - "поиск в заголовках [окно справки]" ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e caps.latest.revision: 9 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="advanced-search-operators-in-search-expressions"></a>Операторы расширенного поиска в выражениях поиска
Используя операторы расширенного поиска в окне справки, можно уточнять поиск содержимого, указывая, где именно в разделе следует искать условие. В приведенной ниже таблице описаны четыре доступных расширенных оператора поиска.

|Условие, которое требуется найти|Применение|Пример|Результат|  
|-------------------|---------|-------------|------------|  
|Термин в заголовке раздела|title:|title:binaryreader|Разделы, содержащие "binaryreader" в заголовках.|  
|Термин в примере кода|code:|code:readdouble|Разделы, содержащие"readdouble" в примере кода.|  
|Термин в примере конкретного языка программирования|code:vb:|code:vb:string|Разделы, содержащие "string", в примере кода Visual Basic.|  
|Раздел, связанный с конкретным ключевым словом индекса|keyword:|keyword:readbyte|Разделы, связанные с ключевым словом индекса "readbyte"|  

> [!WARNING]
>  Операторы расширенного поиска вводятся с двоеточием на конце и без промежуточных пробелов перед двоеточием: только так поисковая система сможет распознать их.    

## <a name="programming-languages-for-code-examples"></a>Языки программирования для примеров кода
Оператор code: можно использовать для поиска сведений о любом из нескольких языков программирования, но он возвращает результаты только для содержимого, которое включает отметку о языке программирования. Чтобы получить примеры для определенного языка программирования, используйте одно из указанных ниже значений.  

|Язык программирования|Синтаксис оператора поиска|  
|--------------------|---------|  
|Visual Basic|code:vb<br/>code:visualbasic|  
|C#|code:c#<br/>code:csharp|  
|C++|code:cpp<br/>code:c++<br/>code:cplusplus|  
|F#|code:f#<br/>code:fsharp|  
|JavaScript|code:javascript<br/>code:js|  
|XAML|code:xaml|
