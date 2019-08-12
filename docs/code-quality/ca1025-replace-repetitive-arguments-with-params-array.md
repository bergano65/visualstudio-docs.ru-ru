---
title: CA1025. Замените повторяющиеся аргументы массивом параметров
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5014bfe809cb5d56a22e971833128d1f48d77319
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922970"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025. Замените повторяющиеся аргументы массивом параметров

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Открытый или защищенный метод в открытом типе имеет более трех параметров, и его последние три параметра имеют один и тот же тип.

## <a name="rule-description"></a>Описание правила
Используйте массив параметров вместо повторяющихся аргументов, если точное число аргументов неизвестно, а аргументы-переменные имеют одинаковый тип или могут передаваться как один и тот же тип. Например, <xref:System.Console.WriteLine%2A> метод предоставляет перегрузку общего назначения, которая использует массив параметров для приема любого <xref:System.Object> числа аргументов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, замените повторяющиеся аргументы массивом параметров.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Всегда можно отключить вывод предупреждения из этого правила. Однако такая схема может вызвать проблемы с удобством использования.

## <a name="example"></a>Пример
В следующем примере показан тип, нарушающий это правило.

[!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]