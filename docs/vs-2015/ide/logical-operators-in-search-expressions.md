---
title: Логические операторы в выражениях поиска | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 66d6aa6a11ef0ce308c5ba2b089aaa8170b6441f
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54760074"
---
# <a name="logical-operators-in-search-expressions"></a>Логические операторы в выражениях поиска
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью логических операторов можно уточнить поиск содержимого путем создания более сложных выражений на основе простых. Как показано в следующей таблице, логические операторы показывают, как следует объединять несколько условий в запросе поиска.  
  
> [!IMPORTANT]
>  Логические операторы необходимо вводить прописными буквами, чтобы поисковая система могла их распознать.  
  
|Условие, которое требуется найти|Использовать|Пример|Результат|  
|-------------------|---------|-------------|------------|  
|Оба условия в одном разделе|AND|dib AND palette|Разделы, содержащие "dib" и "palette".|  
|Любое из условий в разделе|OR|raster OR vector|Разделы, содержащие либо "raster", либо "vector".|  
|Первое условие без второго условия в одном разделе|NOT|"operating system" NOT DOS|Разделы, содержащие "operating system", но не "DOS".|  
|Оба условия, находящиеся близко друг к другу в разделе|БЛИЗКО|user NEAR kernel|Разделы, содержащие "user" недалеко от "kernel".|  
  
## <a name="see-also"></a>См. также раздел  
 [Советы по полнотекстовому поиску](../ide/full-text-search-tips.md)   
 [Поиск сведений](../ide/locate-information.md)
