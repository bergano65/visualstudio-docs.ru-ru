---
title: 'CA1025: Замените повторяющиеся аргументы массивом параметров | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: a9d42e7109d75f14d51e0e7834bc996f6f8864dc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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