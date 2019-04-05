---
title: Анонимные методы и анализ кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b8b3f64a0b5f70067367e98d7e1d1471fc670099
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979172"
---
# <a name="anonymous-methods-and-code-analysis"></a>Анонимные методы и анализ кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Анонимный метод* — это метод, который не имеет имени. Анонимные методы часто используются для передачи блока кода в качестве аргумента делегата.  
  
 В этом разделе объясняется, как анализ кода обрабатывает предупреждения и метрики, которые связаны с анонимными методами.  
  
## <a name="anonymous-methods-declared-in-a-member"></a>Анонимные методы, объявленные в элементе  
 Предупреждения и метрики для анонимного метода, объявленного в члене, например, метод или метод доступа, связаны с членом, который объявляет метод. Они не связаны с членом, который вызывает метод.  
  
 Например, в следующем классе все предупреждения, которые находятся в объявлении **anonymousMethod** должен вызываться по отношению **Method1** и не **Method2**.  
  
```vb  
  
      Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5  
        Method2(anonymousMethod)  
    End SubSub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End SubEnd Class  
```  
  
```csharp  
  
      delegate void Delegate();  
class Class  
{  
    void Method1()  
    {  
        Delegate anonymousMethod = delegate()   
        {   
          Console.WriteLine("");   
        }  
        Method2(anonymousMethod);  
    }  
  
    void Method2(Delegate anonymousMethod)  
    {  
        anonymousMethod();  
    }  
}  
```  
  
## <a name="inline-anonymous-methods"></a>Встроенные анонимные методы  
 Предупреждения и метрики для анонимного метода, объявленного как встроенное назначение полю связаны с конструктором. Если поле объявляется как `static` (`Shared` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), предупреждения и метрики, связанные с конструктором класса; в противном случае, они связаны с конструктором экземпляра.  
  
 Например, в следующем классе все предупреждения, которые находятся в объявлении **anonymousMethod1** будет вызываться по отношению конструктор неявно создаваемый по умолчанию **класс**. Тогда как все предупреждения, найденные в **анонимного метода anonymousMethod2** нужно применять конструктор неявно создаваемый класс.  
  
```vb  
  
  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End SubEnd Class  
```  
  
```csharp  
  
      delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod1 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    static Delegate anonymousMethod2 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    void Method()  
    {  
       anonymousMethod1();  
       anonymousMethod2();  
    }  
}  
```  
  
 Класс может содержать встроенный анонимный метод, который присваивает значение полю, которое имеет несколько конструкторов. В этом случае предупреждения и метрики, связанные со всеми конструкторами, если конструктор связан с другим конструктором, в том же классе.  
  
 Например, в следующем классе все предупреждения, которые находятся в объявлении **anonymousMethod** должен вызываться по отношению **Class(int)** и **Class(string)** , но не для **Class()**.  
  
```vb  
  
  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
SubNew()  
    New(CStr(Nothing))  
End SubSub New(ByVal a As Integer)  
End SubSub New(ByVal a As String)  
End SubEnd Class  
```  
  
```csharp  
  
      delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    Class() : this((string)null)  
    {  
    }  
  
    Class(int a)  
    {  
    }  
  
    Class(string a)  
    {  
    }  
}  
```  
  
 Несмотря на то, что это может показаться Непредвиденная, это происходит потому, что компилятор создает уникальный метод для каждого конструктора, не существует цепочки другого конструктора. Из-за этого поведения, все нарушения, выполняемая в **anonymousMethod** должны подавляться отдельно. Это также означает, что если новый конструктор появился, предупреждения, которые ранее были скрыты от **Class(int)** и **Class(string)** должны подавляться для нового конструктора.  
  
 Можно обойти эту проблему в одном из двух способов. Вы можете объявить **anonymousMethod** в общем конструкторе, все цепочки конструкторов. Или вы можете объявить в методе инициализации, который вызывается конструкторами всех.  
  
## <a name="see-also"></a>См. также  
 [Анализ качества управляемого кода](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
