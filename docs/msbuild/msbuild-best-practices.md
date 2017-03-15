---
title: "Рекомендации по MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "рекомендации, MSBuild"
  - "MSBuild, рекомендации"
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# Рекомендации по MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

При создании скриптов MSBuild рекомендуется следовать следующим правилам.  
  
-   Для более эффективной обработки значений свойств по умолчанию рекомендуется использовать атрибут `Condition`, а не объявлять свойство, значение по умолчанию которого можно переопределить в командной строке.  Например, используйте  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   При выборе элементов избегайте подстановочных знаков.  Файлы необходимо указывать явным образом.  Это упрощает процесс отслеживания ошибок, которые могут возникнуть при добавлении или удалении файлов.  
  
## См. также  
 [Дополнительные возможности](../msbuild/msbuild-advanced-concepts.md)