---
title: 'CA1025: замена повторяющихся аргументов массивом params | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 84809341d7898aeb3defe0447f2a2f1142eb460a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546631"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025. Замените повторяющиеся аргументы массивом параметров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод в открытом типе имеет более трех параметров, и его последние три параметра имеют один и тот же тип.

## <a name="rule-description"></a>Описание правила
 Используйте массив параметров вместо повторяющихся аргументов, если точное число аргументов неизвестно, а аргументы-переменные имеют одинаковый тип или могут передаваться как один и тот же тип. Например, <xref:System.Console.WriteLine%2A> метод предоставляет перегрузку общего назначения, которая использует массив параметров для приема любого числа <xref:System.Object> аргументов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, замените повторяющиеся аргументы массивом параметров.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Всегда можно отключить вывод предупреждения из этого правила. Однако такая схема может вызвать проблемы с удобством использования.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий это правило.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]
