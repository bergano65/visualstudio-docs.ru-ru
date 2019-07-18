---
title: CA1501. Избегайте излишнего наследования | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 420e9492fc5ab431710d62e1d8ea3c1bd8a31ce9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191482"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501. Избегайте излишнего наследования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|Категория|Microsoft.Maintainability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип расположен глубже четырех уровней в иерархии наследования.

## <a name="rule-description"></a>Описание правила
 Глубокие иерархии вложенных типов трудно отслеживать, понимать и поддерживать. Это правило ограничивает Анализ иерархий в одном модуле.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, создать производный тип от базового типа, который является менее вложенности в иерархии наследования или исключить некоторые из промежуточных базовых типов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила. Тем не менее код может быть более сложным в обслуживании. Обратите внимание на то, что, в зависимости от видимости базовых типов, устранение нарушений данного правила могут создать критические изменения. Например удаление открытых базовых типов является критическим изменением.

## <a name="example"></a>Пример
 В примере показан тип, который нарушает правило.

 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/cs/FxCop.Maintainability.ExcessiveInheritance.cs#1)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/vb/FxCop.Maintainability.ExcessiveInheritance.vb#1)]
