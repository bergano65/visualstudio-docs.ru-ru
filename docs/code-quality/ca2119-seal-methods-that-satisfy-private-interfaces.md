---
title: "CA2119: запечатайте методы, соответствующие частным интерфейсам | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SealMethodsThatSatisfyPrivateInterfaces"
  - "CA2119"
helpviewer_keywords: 
  - "CA2119"
  - "SealMethodsThatSatisfyPrivateInterfaces"
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2119: запечатайте методы, соответствующие частным интерфейсам
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|  
|CheckId|CA2119|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Наследуемый отрытый тип предоставляет реализацию переопределяемого метода интерфейса `internal` \(`Friend` в Visual Basic\).  
  
## Описание правила  
 Методы интерфейса являются открытыми для доступа, чего нельзя изменить путем реализации типа.  Внутренний интерфейс создает контракт, который не предназначен для реализации вне сборки, определяющей интерфейс.  Открытый тип, реализующий метод внутреннего интерфейса при помощи модификатора `virtual` \(`Overridable` в Visual Basic\) позволяет переопределять метод производным типам, находящимся вне сборки.  Если второй тип в определяющей сборке вызывает метод и требует только внутреннего контракта, поведение может быть нарушено, если будет выполнен переопределенный метод во внешней сборке.  Это создает уязвимость безопасности.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, избегайте переопределения метода вне сборки, выполнив одно из следующих действий.  
  
-   Сделайте объявляющий тип `sealed` \(`NotInheritable` в Visual Basic\).  
  
-   Измените доступность объявляющего типа на `internal` \(`Friend` в Visual Basic\).  
  
-   Удалите все открытые конструкторы из объявляющего типа.  
  
-   Реализуйте метод без модификатора `virtual`.  
  
-   Реализуйте метод явным образом.  
  
## Отключение предупреждений  
 Предупреждение из этого правила можно отключить без последствий при условии, что после тщательного анализа отсутствуют угрозы безопасности, которые могли бы быть использованы, если бы метод переопределялся вне сборки.  
  
## Пример  
 В следующем примере показан тип `BaseImplementation`, который нарушает данное правило.  
  
 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-cs[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]  
  
## Пример  
 В следующем примере используется реализация виртуального метода из предыдущего примера.  
  
 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-cs[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]  
  
## См. также  
 [Интерфейсы](/dotnet/csharp/programming-guide/interfaces/index)   
 [Интерфейсы](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)