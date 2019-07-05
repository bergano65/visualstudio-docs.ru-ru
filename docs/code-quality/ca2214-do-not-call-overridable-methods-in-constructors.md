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
ms.openlocfilehash: 8e05e6925085b27de3001c8ff62d8a3c6e69a88f
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401315"
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

> [!NOTE]
> Реализация двоичный анализ это правило имеет разные диагностическое сообщение из " **\[имя конструктора] содержит цепочку вызовов, который приводит к вызову виртуального метода, определяемый классом. Просмотрите следующий стек вызовов для обнаружения непреднамеренных последствий**«. [Анализаторы FxCop](install-fxcop-analyzers.md) реализации этого правила есть диагностическое сообщение из "**не вызывайте переопределяемые методы в конструкторах**«.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, не следует вызывать виртуальные методы типа из конструкторов типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует. Конструктор, должны быть переработаны во избежание вызов виртуального метода.

## <a name="example"></a>Пример

В следующем примере показано влияние нарушения этого правила. Тестовое приложение создает экземпляр класса `DerivedType`, что приводит его базового класса (`BadlyConstructedType`) конструктор для выполнения. `BadlyConstructedType`в конструктор неправильно вызывает виртуальный метод `DoSomething`. Как показывает вывод, `DerivedType.DoSomething()` выполняются перед `DerivedType`выполняется конструктор.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

В этом примере выводятся следующие данные:

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```