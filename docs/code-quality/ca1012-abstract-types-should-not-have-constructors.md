---
title: "CA1012: Абстрактные типы не должны иметь конструкторы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 42c0309181dbea76826aafb67b33579e2bd3ae78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012: абстрактные типы не должны иметь конструкторы
|||  
|-|-|  
|TypeName|AbstractTypesShouldNotHaveConstructors|  
|CheckId|CA1012|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Открытый тип является абстрактным и имеет открытый конструктор.  
  
## <a name="rule-description"></a>Описание правила  
 Конструкторы абстрактных типов могут быть вызваны только производными типами. Открытые конструкторы создают экземпляры типа. Невозможно создавать экземпляры абстрактного типа; абстрактный тип с открытым конструктором является недопустимым.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, сделайте конструктор защищенным или не объявляйте тип абстрактным.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует. Абстрактный тип имеет открытый конструктор.  
  
## <a name="example"></a>Пример  
 Следующий пример содержит абстрактный тип, нарушающий это правило.  
  
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]  
  
## <a name="example"></a>Пример  
 В следующем примере предыдущее нарушение устраняется путем изменения специальные возможности конструктора из `public` для `protected`.  
  
 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]