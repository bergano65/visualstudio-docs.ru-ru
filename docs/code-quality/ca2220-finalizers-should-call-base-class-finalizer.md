---
title: CA2220. Методы завершения должны вызывать метод завершения базового класса
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30892ce84e1370aec06e73a51f47c3de66dfa620
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998187"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220. Методы завершения должны вызывать метод завершения базового класса

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип, который переопределяет <xref:System.Object.Finalize%2A?displayProperty=fullName> не вызывает <xref:System.Object.Finalize%2A> метод в базовом классе.

## <a name="rule-description"></a>Описание правила

Финализация должна распространятся посредством иерархии наследования. Для этого типы должны вызывать базовый класс <xref:System.Object.Finalize%2A> метода в свои собственные <xref:System.Object.Finalize%2A> метод. Компилятор C# автоматически добавляет вызов метод завершения базового класса.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, вызовите базовый тип <xref:System.Object.Finalize%2A> метода из вашей <xref:System.Object.Finalize%2A> метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует. Некоторые компиляторы, предназначенные среда CLR вставьте вызов метод завершения базового типа в промежуточный язык Майкрософт (MSIL). Если выводится предупреждение из этого правила, компилятор не вставляет вызов, и его необходимо добавить в код.

## <a name="example"></a>Пример

В следующем примере Visual Basic показан тип `TypeB` , правильно вызывает <xref:System.Object.Finalize%2A> метод в базовом классе.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>См. также

- [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)