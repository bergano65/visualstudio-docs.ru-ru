---
title: 'CA1821: удаляйте пустые методы завершения'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f24b0f4c6358da459525288a2812446c1c73f3d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: удаляйте пустые методы завершения
|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип реализует метод завершения, который является пустым, вызывает только метод завершения базового типа или вызывает только условно создаваемые методы.

## <a name="rule-description"></a>Описание правила
 Если возможно, старайтесь не использовать финализаторы, поскольку из-за отслеживания жизненного срока объектов снижается производительность программы. Сборщик мусора запустит метод завершения, прежде чем она собирает объекта. Это означает, что две коллекции необходимо, чтобы объект. Пустой метод завершения влечет за собой дополнительных издержек без никаких преимуществ.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите пустой метод завершения. Если метод завершения является обязательным для отладки, заключите весь метод завершения в `#if DEBUG / #endif` директивы.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте сообщение из этого правила. Сбой для подавления финализации снижает производительность и не дает преимущества.

## <a name="example"></a>Пример
 В следующем примере показано пустой метод завершения, который должен быть удален, метод завершения, который должен быть заключен в `#if DEBUG / #endif` директивы и метод завершения, который использует `#if DEBUG / #endif` директивы правильно.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]