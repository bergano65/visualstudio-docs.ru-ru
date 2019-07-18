---
title: CA1025. Замените повторяющиеся аргументы массивом параметров | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 83d36f1f5cd31b1ad1833dd805f4386ac71a3ed1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68144796"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025. Замените повторяющиеся аргументы массивом параметров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]
