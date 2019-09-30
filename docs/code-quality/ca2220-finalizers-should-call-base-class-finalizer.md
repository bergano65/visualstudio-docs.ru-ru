---
title: CA2220. Методы завершения должны вызывать метод завершения базового класса
ms.date: 11/04/2016
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
ms.openlocfilehash: e5af6b7872f0fa05183334e6acd2bc4922f84990
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231158"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220. Методы завершения должны вызывать метод завершения базового класса

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Тип, переопределяющий <xref:System.Object.Finalize%2A?displayProperty=fullName> , не <xref:System.Object.Finalize%2A> вызывает метод в его базовом классе.

## <a name="rule-description"></a>Описание правила

Финализация должна распространятся посредством иерархии наследования. Чтобы убедиться в этом, типы должны вызывать свой метод <xref:System.Object.Finalize%2A> базового класса из своего собственного <xref:System.Object.Finalize%2A> метода. C# Компилятор автоматически добавляет вызов метода завершения базового класса.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, вызовите <xref:System.Object.Finalize%2A> метод базового типа <xref:System.Object.Finalize%2A> из метода.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует. Некоторые компиляторы, нацеленные на среду CLR, вставляют вызов метода завершения базового типа в промежуточный язык Майкрософт (MSIL). Если выводится предупреждение из этого правила, компилятор не вставляет вызов, и его необходимо добавить в код.

## <a name="example"></a>Пример

В следующем примере Visual Basic показан тип `TypeB` , который правильно <xref:System.Object.Finalize%2A> вызывает метод в базовом классе.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>См. также

- [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)