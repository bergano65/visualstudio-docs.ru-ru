---
title: 'CA1012: Абстрактные типы не должны иметь конструкторы | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b10d41b9671b3f25aea6722835d709b24ab9b12
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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