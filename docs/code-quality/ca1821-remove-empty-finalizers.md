---
title: CA1821. Удалите пустые методы завершения
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c8c4d4ca04c7a9a21cd1e80e4dc06e8d5a92c2f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921373"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821. Удалите пустые методы завершения

|||
|-|-|
|TypeName|ремовимптифинализерс|
|CheckId|CA1821|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Тип реализует метод завершения, который является пустым, вызывает только метод завершения базового типа или вызывает только условно порожденные методы.

## <a name="rule-description"></a>Описание правила
Если возможно, старайтесь не использовать финализаторы, поскольку из-за отслеживания жизненного срока объектов снижается производительность программы. Сборщик мусора будет запускать метод завершения перед сбором объекта. Это означает, что для сбора объекта потребуется две коллекции. Пустой метод завершения включает в себя дополнительную нагрузку без каких бы то ни было преимуществ.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Удалите пустой метод завершения. Если для отладки требуется метод завершения, заключите весь метод завершения в `#if DEBUG / #endif` директивы.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Не отключайте сообщение от этого правила. Сбой отключения финализации снижает производительность и не дает никаких преимуществ.

## <a name="example"></a>Пример
В следующем примере показан пустой метод завершения, который следует удалить, метод завершения, который должен быть заключен в `#if DEBUG / #endif` директивы, и метод завершения, который правильно использует эти `#if DEBUG / #endif` директивы.

[!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]