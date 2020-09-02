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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d56f2dfc2924008a6be293fe1498f0ffe32abaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651439"
---
# <a name="logical-operators-in-search-expressions"></a>Логические операторы в выражениях поиска
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью логических операторов можно уточнить поиск содержимого путем создания более сложных выражений на основе простых. Как показано в следующей таблице, логические операторы показывают, как следует объединять несколько условий в запросе поиска.

> [!IMPORTANT]
> Логические операторы необходимо вводить прописными буквами, чтобы поисковая система могла их распознать.

|Условие, которое требуется найти|Использование|Пример|Результат|
|-------------------|---------|-------------|------------|
|Оба условия в одном разделе|AND|dib AND palette|Разделы, содержащие "dib" и "palette".|
|Любое из условий в разделе|OR|raster OR vector|Разделы, содержащие либо "raster", либо "vector".|
|Первое условие без второго условия в одном разделе|NOT|"operating system" NOT DOS|Разделы, содержащие "operating system", но не "DOS".|
|Оба условия, находящиеся близко друг к другу в разделе|NEAR|user NEAR kernel|Разделы, содержащие "user" недалеко от "kernel".|

## <a name="see-also"></a>См. также:
 [Советы по полнотекстовому поиску](../ide/full-text-search-tips.md) . [Поиск информации](../ide/locate-information.md)
