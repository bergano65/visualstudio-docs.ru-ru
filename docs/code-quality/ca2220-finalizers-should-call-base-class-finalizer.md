---
title: 'CA2220: Методы завершения должны вызывать метод завершения базового класса | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b2d5181e04a9a44516716ff280802eb5232f8da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: методы завершения должны вызывать метод завершения базового класса
|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Тип, который переопределяет <xref:System.Object.Finalize%2A?displayProperty=fullName> не вызывает <xref:System.Object.Finalize%2A> метод в базовом классе.  
  
## <a name="rule-description"></a>Описание правила  
 Финализация должна распространятся посредством иерархии наследования. Чтобы обеспечить это, типы должны вызывать их базовым классом <xref:System.Object.Finalize%2A> метода в своих собственных <xref:System.Object.Finalize%2A> метод. Компилятор C# автоматически добавляет вызов метод завершения базового класса.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, вызовите метод базового типа <xref:System.Object.Finalize%2A> метода из вашего <xref:System.Object.Finalize%2A> метод.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует. Некоторые компиляторы, работающие среда вставить вызов метод завершения базового типа в промежуточный язык Microsoft (MSIL). Если выводится предупреждение из этого правила, компилятор не вставляет вызов, и необходимо добавить его в код.  
  
## <a name="example"></a>Пример  
 В следующем примере Visual Basic показан тип `TypeB` правильно вызывает <xref:System.Object.Finalize%2A> метод в базовом классе.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## <a name="see-also"></a>См. также  
 [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)