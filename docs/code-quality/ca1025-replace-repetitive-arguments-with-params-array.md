---
title: 'CA1025: замените повторяющиеся аргументы массивом параметров'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1ce14b7da80775a9837b5e92f25d141276226cf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900519"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: замените повторяющиеся аргументы массивом параметров
|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод в открытом типе имеет более трех параметров, а последние три параметра относятся к одному типу.

## <a name="rule-description"></a>Описание правила
 Если точное число аргументов неизвестно и эти аргументы относятся к одному типу или могут быть переданы как тот же тип, используйте вместо повторяющихся аргументов массив параметров. Например <xref:System.Console.WriteLine%2A> метод предоставляет общего назначения перегрузку, которая использует массив параметров, чтобы принимать любое количество <xref:System.Object> аргументы.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, замените повторяющиеся аргументы массивом параметров.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Всегда можно безопасно подавить предупреждение из этого правила; Однако такой подход может вызвать проблемы удобство использования.

## <a name="example"></a>Пример
 В следующем примере показано тип, нарушающий это правило.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]