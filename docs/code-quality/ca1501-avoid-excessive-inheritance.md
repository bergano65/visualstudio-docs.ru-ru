---
title: 'CA1501: избегайте излишнего наследования'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62270ac1917dea24586247ade5f8f5e802f84707
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914397"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: избегайте излишнего наследования
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
 Чтобы устранить нарушение данного правила, сделайте тип производным от базового типа, который меньше вложенности в иерархии наследования или исключить некоторые из промежуточных базовых типов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила. Тем не менее код может быть более сложным в обслуживании. Обратите внимание, что, в зависимости от видимости базовых типов, устранение нарушений данного правила может создавать критические изменения. Например удаление открытых базовых типов является критическим изменением.

## <a name="example"></a>Пример
 В следующем примере показано тип, нарушающий правило.

 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]