---
title: 'CA1821: удаление пустых методов завершения | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3d340d69ee32de20142abf740f7fedc871c9733a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657476"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: удаляйте пустые методы завершения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 Удалите пустой метод завершения. Если для отладки требуется метод завершения, заключите весь метод завершения в директивы `#if DEBUG / #endif`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте сообщение от этого правила. Сбой отключения финализации снижает производительность и не дает никаких преимуществ.

## <a name="example"></a>Пример
 В следующем примере показан пустой метод завершения, который следует удалить, метод завершения, который должен быть заключен в директивы `#if DEBUG / #endif`, и метод завершения, который правильно использует директивы `#if DEBUG / #endif`.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]
