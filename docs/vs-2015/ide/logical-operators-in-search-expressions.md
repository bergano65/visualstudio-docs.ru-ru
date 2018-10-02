---
title: Логические операторы в выражениях поиска | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0cf55bbdc025b4aabd13f7ded72c2ea69386a61b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559343"
---
# <a name="logical-operators-in-search-expressions"></a>Логические операторы в выражениях поиска
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [логические операторы в выражениях поиска](https://docs.microsoft.com/visualstudio/ide/logical-operators-in-search-expressions).  
  
С помощью логических операторов можно уточнить поиск содержимого путем создания более сложных выражений на основе простых. Как показано в следующей таблице, логические операторы показывают, как следует объединять несколько условий в запросе поиска.  
  
> [!IMPORTANT]
>  Логические операторы необходимо вводить прописными буквами, чтобы поисковая система могла их распознать.  
  
|Условие, которое требуется найти|Использовать|Пример|Результат|  
|-------------------|---------|-------------|------------|  
|Оба условия в одном разделе|AND|dib AND palette|Разделы, содержащие "dib" и "palette".|  
|Любое из условий в разделе|OR|raster OR vector|Разделы, содержащие либо "raster", либо "vector".|  
|Первое условие без второго условия в одном разделе|NOT|"operating system" NOT DOS|Разделы, содержащие "operating system", но не "DOS".|  
|Оба условия, находящиеся близко друг к другу в разделе|БЛИЗКО|user NEAR kernel|Разделы, содержащие "user" недалеко от "kernel".|  
  
## <a name="see-also"></a>См. также  
 [Советы по полнотекстовому поиску](../ide/full-text-search-tips.md)   
 [Поиск сведений](../ide/locate-information.md)



