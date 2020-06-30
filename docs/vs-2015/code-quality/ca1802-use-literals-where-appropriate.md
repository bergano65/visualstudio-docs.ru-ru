---
title: 'CA1802: Используйте литералы там, где это уместно | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dc8019c97d3c561000f1c6a8d083bee6253face3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544408"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802. По возможности используйте литералы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Поле объявляется `static` и `readonly` ( `Shared` и `ReadOnly` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) и инициализируется со значением, вычисляемым во время компиляции.

## <a name="rule-description"></a>Описание правила
 Значение `static``readonly` поля вычисляются во время выполнения, когда вызывается статический конструктор для объявляющего типа. Если `static``readonly` поле инициализируется при объявлении и статический конструктор не объявлен явным образом, компилятор создает статический конструктор для инициализации поля.

 Значение `const` поля вычисляются во время компиляции и сохраняется в метаданных, что повышает производительность среды выполнения при сравнении с `static``readonly` полем.

 Так как значение, назначенное целевому полю, вычисляемым во время компиляции, измените объявление на `const` поле, чтобы значение было вычислено во время компиляции, а не в среде выполнения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, замените `static` `readonly` модификаторы и `const` модификатором.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила или отключать правило, если производительность не важна.

## <a name="example"></a>Пример
 В следующем примере показан тип, `UseReadOnly` , который нарушает правило и тип, `UseConstant` который удовлетворяет правилу.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
