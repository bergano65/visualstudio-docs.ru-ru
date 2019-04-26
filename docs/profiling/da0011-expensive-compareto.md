---
title: DA0011. Затратный метод CompareTo | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee5839e91e2205a98a38ed27823a26a4a127e1ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936591"
---
# <a name="da0011-expensive-compareto"></a>DA0011. Затратный метод CompareTo

|||
|-|-|
|Идентификатор правила|DA0011|
|Категория|Использование .NET Framework|
|Методы профилирования|Дискретизация<br /><br /> Память .NET|
|Сообщение|Функции CompareTo должны быть малозатратными и не выделять память. Если возможно, уменьшите сложность функции CompareTo.|
|Тип правила|Предупреждение|

## <a name="cause"></a>Причина
 Метод CompareTo типа является затратным или выделяет память.

## <a name="rule-description"></a>Описание правила
 Методы CompareTo должны быть эффективными и не выделять память.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Упростите метод CompareTo.