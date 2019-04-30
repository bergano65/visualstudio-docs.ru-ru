---
title: CA2214. Не вызывайте переопределяемые методы в конструкторах
ms.date: 11/04/2016
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
ms.openlocfilehash: ef2a5631247f882a70ae94877da02f576ff04a5d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796709"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214. Не вызывайте переопределяемые методы в конструкторах

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Конструктор незапечатанный тип вызывает виртуальный метод, определенный в классе.

## <a name="rule-description"></a>Описание правила

При вызове виртуального метода фактический тип, который выполняет метод не выбран до времени выполнения. Когда конструктор вызывает виртуальный метод, вполне возможно, что конструктор экземпляра, который вызывает метод не выполнен.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, не следует вызывать виртуальные методы типа из конструкторов типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует. Конструктор, должны быть переработаны во избежание вызов виртуального метода.

## <a name="example"></a>Пример

В следующем примере показано влияние нарушения этого правила. Тестовое приложение создает экземпляр класса `DerivedType`, что приводит его базового класса (`BadlyConstructedType`) конструктор для выполнения. `BadlyConstructedType`в конструктор неправильно вызывает виртуальный метод `DoSomething`. Как показывает вывод, `DerivedType.DoSomething()` выполняет и поэтому сначала выполняет `DerivedType`выполняется конструктор.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

В этом примере выводятся следующие данные:

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```