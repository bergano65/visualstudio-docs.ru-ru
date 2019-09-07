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
ms.openlocfilehash: f616547738c7c58d61289b2be71c8e56a1a427c8
ms.sourcegitcommit: 0f44ec8ba0263056ad04d2d0dc904ad4206ce8fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70766074"
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

Всякий раз, когда это возможно, Избегайте методов завершения из-за дополнительных затрат на производительность, связанных с отслеживанием времени существования объектов. Сборщик мусора запускает метод завершения перед сбором объекта. Это означает, что для сбора объекта требуется по крайней мере две коллекции. Пустой метод завершения включает в себя дополнительную нагрузку без каких бы то ни было преимуществ.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Удалите пустой метод завершения. Если для отладки требуется метод завершения, заключите весь метод завершения в `#if DEBUG / #endif` директивы.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Не отключайте сообщение от этого правила.

## <a name="example"></a>Пример

В следующем примере показан пустой метод завершения, который следует удалить, метод завершения, который должен быть заключен в `#if DEBUG / #endif` директивы, и метод завершения, который правильно использует эти `#if DEBUG / #endif` директивы.

[!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]
