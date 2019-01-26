---
title: CA1821. Удалите пустые методы завершения
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 01f89e022be966f0d265abd2f4e24b1779ce64b1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975183"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821. Удалите пустые методы завершения

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип реализует метод завершения, который является пустым, вызывает только метод завершения базового типа или вызывает только условно создаваемые методы.

## <a name="rule-description"></a>Описание правила
 Если возможно, старайтесь не использовать финализаторы, поскольку из-за отслеживания жизненного срока объектов снижается производительность программы. Сборщик мусора будет выполняться метод завершения, прежде чем он собирает объекта. Это означает, что две коллекции требуется для сбора объекта. Пустой метод завершения влечет за собой дополнительных издержек без каких-либо преимуществ.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите пустой метод завершения. Если метод завершения не требуется для отладки, заключите весь метод завершения подобным `#if DEBUG / #endif` директивы.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте сообщение из этого правила. Неотключенные снижает производительность и не дает преимуществ.

## <a name="example"></a>Пример
 В следующем примере показано пустой метод завершения, который должен быть удален, метод завершения, который должен быть заключен в `#if DEBUG / #endif` директивы и метод завершения, который использует `#if DEBUG / #endif` директивы правильно.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]