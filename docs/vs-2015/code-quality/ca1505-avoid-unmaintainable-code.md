---
title: 'CA1505: Избегайте неподдерживаемого кода | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 87aacfd675181e35d289b2a054c58f83f3f790fa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607589"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505. Избегайте кода, неудобного для поддержки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|авоидунмантаинаблекоде|
|CheckId|CA1505|
|Категория|Поддержка Microsoft.|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип или метод имеет низкий индекс обслуживаемости.

## <a name="rule-description"></a>Описание правила
 Индекс удобства обслуживания вычисляется с помощью следующих метрик: строк кода, программного тома и сложности сложностью организации циклов. Программный том — это мера сложности понимания типа или метода, основанного на количестве операторов и операндов в коде. Сложностью организации циклов сложность — это мера структурной сложности типа или метода. Дополнительные сведения о метриках кода см. в статье [измерение сложности и удобство сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

 Низкий индекс удобства обслуживания означает, что тип или метод, вероятно, трудно обслуживать, и это будет хорошим кандидатом к перепроектированию.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить это нарушение, повторно Разработайте тип или метод и попытайтесь разделить его на небольшие и более мелкие типы или методы.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Исключите это предупреждение, если тип или метод по-прежнему считается обслуживаемым, несмотря на большой размер или если тип или метод не могут быть разделены.

## <a name="see-also"></a>См. также раздел
 [Предупреждения о поддержке](../code-quality/maintainability-warnings.md) [, измеряющие сложность и удобство сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
