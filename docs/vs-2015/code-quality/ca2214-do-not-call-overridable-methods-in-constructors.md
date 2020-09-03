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
ms.openlocfilehash: ad467e880b3281a75db2627108af0e0b2f90ea99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534463"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214. Не вызывайте переопределяемые методы в конструкторах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
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
 В следующем примере показан результат нарушения этого правила. Тестовое приложение создает экземпляр `DerivedType` , который приводит к выполнению его базового класса ( `BadlyConstructedType` ). `BadlyConstructedType`неправильно вызывает виртуальный метод `DoSomething` . Как видно из выходных данных, `DerivedType.DoSomething()` выполняет и делает это до `DerivedType` выполнения конструктора.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 В этом примере формируются следующие данные:

 **Вызов базового ctor.** 
 **Производный DoSomething называется-Initialized? Не** 
 **вызывается производный ctor.**
