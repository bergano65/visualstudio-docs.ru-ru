---
title: 'CA2214: не Вызывайте переопределяемые методы в конструкторах | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 78702298bab484a95bb8108150415ec0b31ede7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662911"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: не вызывайте переопределяемые методы в конструкторах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, не вызывайте виртуальные методы типа в конструкторах типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Конструктор должен быть переработан, чтобы исключить вызов виртуального метода.

## <a name="example"></a>Пример
 В следующем примере показан результат нарушения этого правила. Тестовое приложение создает экземпляр `DerivedType`, что приводит к выполнению его базового класса (`BadlyConstructedType`). Конструктор `BadlyConstructedType` неправильно вызывает виртуальный метод `DoSomething`. Как видно из выходных данных, `DerivedType.DoSomething()` выполняется и делает это до выполнения конструктора `DerivedType`.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 В этом примере формируются следующие данные:

 **Вызов базового ctor.** 
**производный DoSomething называется-Initialized? Нет** 
**вызова производного ctor.**
