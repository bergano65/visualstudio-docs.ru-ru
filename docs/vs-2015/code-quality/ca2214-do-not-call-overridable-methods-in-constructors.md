---
title: 'CA2214: Не вызывайте переопределяемые методы в конструкторах | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f1ccd614eb14e47401ebab23e41b53679ac2b082
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240426"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: не вызывайте переопределяемые методы в конструкторах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 В этом примере формируются следующие данные:

 **Вызывает базовый конструктор. ** 
 **Называется производным DoSomething - инициализирован? Не**
**вызова производным ctor.**



