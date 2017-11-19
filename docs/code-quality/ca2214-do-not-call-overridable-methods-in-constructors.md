---
title: "CA2214: Не вызывайте переопределяемые методы в конструкторах | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bbe640ac82c159b39721ddac27b9d65926c60647
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
  
 **Вызов базового конструктора.**  
**Вызывается производном DoSomething - инициализирован? Нет**  
**Производный вызов ctor.**