---
title: 'CA1040: Избегайте пустых интерфейсов | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 26ba25038baf0d54c1705d4f4dd6c9b0cca9f856
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: избегайте пустых интерфейсов
|||  
|-|-|  
|TypeName|AvoidEmptyInterfaces|  
|CheckId|CA1040|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Интерфейс не объявляет никаких элементов или реализовывать несколько интерфейсов.  
  
## <a name="rule-description"></a>Описание правила  
 Интерфейсы определяют члены, предоставляющие поведение или соглашение об использовании. Функциональность, описанная интерфейсом, может быть использована любым типом вне зависимости от расположения типа в иерархии интерфейса. Тип реализует интерфейс путем предоставления реализаций для членов интерфейса. Пустой интерфейс не определяет никаких элементов. Таким образом он не определяет контракт, который может быть реализован.  
  
 Если проект содержит пустой интерфейсы, типы должны быть реализованы, как маркер или для определения группы типов, возможно, вы используете интерфейс. Если этот код будет выполняться во время выполнения, правильный способ выполнения этой задачи является использование настраиваемого атрибута. Используйте наличие или отсутствие атрибута или свойства атрибута для определения целевых типов. Если определение должно произойти во время компиляции, он будет доступен для использования пустой интерфейс.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Удалите интерфейс или добавьте в него члены. Если пустой интерфейс используется для обозначения набора типов, замените интерфейс настраиваемого атрибута.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно отключать предупреждение из этого правила, если этот интерфейс используется для идентификации набора типов во время компиляции.  
  
## <a name="example"></a>Пример  
 В следующем примере пустой интерфейс.  
  
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]