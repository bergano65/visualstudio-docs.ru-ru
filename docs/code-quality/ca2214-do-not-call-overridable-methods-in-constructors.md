---
title: 'CA2214: не вызывайте переопределяемые методы в конструкторах'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b5ebcd4164f9db28d4cb1f150ee3a4bb21b21cde
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: не вызывайте переопределяемые методы в конструкторах
|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Конструктор незапечатанного типа вызывает виртуальный метод, определенный в классе.

## <a name="rule-description"></a>Описание правила
 При вызове виртуального метода фактический тип, то метод выполняется только во время выполнения не выбран. Когда конструктор вызывает виртуальный метод, возможна, конструктор экземпляра, который вызывает метод не выполнялся.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, не вызывайте виртуальные методы типа из конструкторов типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Нужно переделать конструктор, устранив вызов виртуального метода.

## <a name="example"></a>Пример
 В следующем примере показано влияние нарушения этого правила. Тестовое приложение создает экземпляр `DerivedType`, которое вызывает его базовый класс (`BadlyConstructedType`) конструктор для выполнения. `BadlyConstructedType`в неправильно, конструктор вызывает виртуальный метод `DoSomething`. Как показывает вывод, `DerivedType.DoSomething()` выполняет и поэтому перед выполняет `DerivedType`выполняется конструктор.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

 В этом примере формируются следующие данные:

 **Вызов базового конструктора. ** 
 **Называется производным DoSomething - инициализирован? Не**
**вызова производный ctor.**