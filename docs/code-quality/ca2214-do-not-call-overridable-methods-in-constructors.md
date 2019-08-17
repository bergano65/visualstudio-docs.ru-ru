---
title: CA2214. Не вызывайте переопределяемые методы в конструкторах
ms.date: 05/29/2016
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a59346cb70269d4d2b405279fc9ea5573a879b1e
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547005"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214. Не вызывайте переопределяемые методы в конструкторах

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Конструктор незапечатанного типа вызывает виртуальный метод, определенный в его классе.

## <a name="rule-description"></a>Описание правила

При вызове виртуального метода фактический тип, который выполняет метод, не выбирается до времени выполнения. Если конструктор вызывает виртуальный метод, возможно, конструктор для экземпляра, который вызывает метод, не выполнялся.

> [!NOTE]
> Реализация традиционного анализа этого правила имеет другое диагностическое сообщение " **\[имя конструктора] содержит цепочку вызовов, которая приводит к вызову виртуального метода, определенного классом. Проверьте следующий стек вызовов для непредвиденных последствий**". В [анализаторе FxCop Analyzer](install-fxcop-analyzers.md) для этого правила имеется диагностическое сообщение "не**вызывать переопределяемые методы в конструкторах**".

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, не вызывайте виртуальные методы типа в конструкторах типа.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует. Конструктор должен быть переработан, чтобы исключить вызов виртуального метода.

## <a name="example"></a>Пример

В следующем примере показан результат нарушения этого правила. Тестовое приложение создает экземпляр `DerivedType`, который приводит к выполнению его базового класса (`BadlyConstructedType`). `BadlyConstructedType`неправильно вызывает виртуальный метод `DoSomething`. Как видно из выходных данных `DerivedType.DoSomething()` , выполняется до `DerivedType`выполнения конструктора.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

В этом примере выводятся следующие данные:

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```