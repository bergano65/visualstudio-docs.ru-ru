---
title: 'CA1048: Не объявляйте виртуальные члены в запечатанных типах | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad16335502394d46eade760ba365b6dcf7ed529c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: не объявляйте виртуальные элементы в запечатанных типах
|||  
|-|-|  
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|  
|CheckId|CA1048|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытый тип является запечатанным и объявляет метод, который является одновременно `virtual` (`Overridable` в Visual Basic) и не последней. Это правило не касается нарушений типов делегатов, которые должны следовать этому шаблону.  
  
## <a name="rule-description"></a>Описание правила  
 Типы объявляют методы как виртуальные, чтобы наследующие типы могли переопределять реализацию виртуального метода. По определению не может наследовать от запечатанного типа, выполняющего виртуальный метод запечатанного типа бессмысленной.  
  
 Компиляторы Visual Basic и C# не позволяют типы нарушение этого правила.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, сделайте метод невиртуальным или сделайте тип наследуемым.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует. Если оставить тип в его текущем состоянии может привести к проблемам в обслуживании и не предоставляет никаких преимуществ.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип, нарушающий это правило.  
  
 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]