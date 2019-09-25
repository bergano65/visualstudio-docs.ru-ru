---
title: CA1061. Не скрывайте методы базовых классов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eacd20dee0758ff481b259807ba52bb78b26f5d2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235391"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061. Не скрывайте методы базовых классов

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Производный тип объявляет метод с тем же именем и с тем же количеством параметров, что и один из его базовых методов. один или несколько параметров являются базовым типом соответствующего параметра в базовом методе. и все остальные параметры имеют типы, идентичные соответствующим параметрам в базовом методе.

## <a name="rule-description"></a>Описание правила
Метод в базовом типе скрыт с помощью метода с идентичным именем в производном типе, когда сигнатура параметра производного метода отличается только типами, которые являются более слабыми, чем соответствующие типы в сигнатуре параметра базового метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, удалите или переименуйте метод или измените сигнатуру параметра таким образом, чтобы метод не скрывал базовый метод.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показан метод, нарушающий правило.

[!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]