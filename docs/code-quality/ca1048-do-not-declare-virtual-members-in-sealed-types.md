---
title: CA1048. Не объявляйте виртуальные члены в запечатанных типах
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 430ed0b23d62bd46a9764bfb0a3834e0decd476b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922597"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048. Не объявляйте виртуальные члены в запечатанных типах

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
Открытый тип запечатан и объявляет метод, который одновременно `virtual` (`Overridable` в Visual Basic) и не является окончательным. Это правило не сообщает о нарушениях типов делегатов, которые должны следовать этому шаблону.

## <a name="rule-description"></a>Описание правила
Типы объявляют методы как виртуальные, чтобы наследующие типы могли переопределять реализацию виртуального метода. По определению нельзя наследовать от запечатанного типа, что делает виртуальный метод запечатанного типа бессмысленным.

Visual Basic и C# компиляторы не позволяют типам нарушать это правило.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, сделайте метод невиртуальным или сделайте тип наследуемым.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует. Если оставить тип в его текущем состоянии, это может вызвать проблемы с обслуживанием и не дает никаких преимуществ.

## <a name="example"></a>Пример
В следующем примере показан тип, нарушающий это правило.

[!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]