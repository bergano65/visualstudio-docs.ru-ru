---
title: CA1025. Замените повторяющиеся аргументы массивом параметров
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: de109dddf3bc0ddb8cd50df8dc27e81111d4b6df
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938514"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025. Замените повторяющиеся аргументы массивом параметров

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод в открытом типе имеет более трех параметров, а последние три параметра относятся к одному типу.

## <a name="rule-description"></a>Описание правила
 Если точное число аргументов неизвестно и эти аргументы принадлежат к одному типу или могут передаваться как тот же тип, используйте вместо повторяющихся аргументов массив параметров. Например <xref:System.Console.WriteLine%2A> метод обеспечивает перегрузки, общего назначения, который использует массив параметров, чтобы принимать любое количество <xref:System.Object> аргументы.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, замените повторяющиеся аргументы массивом параметров.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его всегда можно безопасно подавить предупреждение из этого правила; Однако такой подход может привести к проблем с удобством использования.

## <a name="example"></a>Пример
 В следующем примере тип, который нарушает это правило.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]