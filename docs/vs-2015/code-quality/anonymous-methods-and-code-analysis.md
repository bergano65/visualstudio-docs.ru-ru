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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49da7d5e7f6a7731a708accb3d52fb6383ff1017
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652228"
---
# <a name="anonymous-methods-and-code-analysis"></a>Анонимные методы и анализ кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Анонимный метод* — это метод без имени. Анонимные методы чаще всего используются для передачи блока кода в качестве параметра делегата.

 В этом разделе объясняется, как анализатор кода обрабатывает предупреждения и метрики, связанные с анонимными методами.

## <a name="anonymous-methods-declared-in-a-member"></a>Анонимные методы, объявленные в члене
 Предупреждения и метрики для анонимного метода, объявленного в элементе, например метод или метод доступа, связаны с членом, который объявляет метод. Они не связаны с членом, который вызывает метод.

 Например, в следующем классе все предупреждения, обнаруженные в объявлении **анонимаусмесод** , должны быть вызваны для **Method1** , а не для **Method2**.

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
 Предупреждения и метрики для анонимного метода, объявленного как встроенное присваивание полю, связываются с конструктором. Если поле объявлено как `static` (`Shared` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), предупреждения и метрики связаны с конструктором класса. в противном случае они связаны с конструктором экземпляра.

 Например, в следующем классе все предупреждения, обнаруженные в объявлении **anonymousMethod1** , будут вызываться для неявно созданного конструктора по умолчанию **класса**. В то время как они найдены в **anonymousMethod2** , будут применяться к неявно созданному конструктору класса.

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

 Класс может содержать встроенный анонимный метод, который присваивает значение полю, имеющему несколько конструкторов. В этом случае предупреждения и метрики связываются со всеми конструкторами, если только этот конструктор не повязывается к другому конструктору в том же классе.

 Например, в следующем классе все предупреждения, обнаруженные в объявлении **анонимаусмесод** , должны вызываться для **класса (int)** и **класса (String)** , но не для **класса ()** .

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

 Хотя это может показаться неожиданным, это происходит из-за того, что компилятор выводит уникальный метод для каждого конструктора, который не поступает в цепочку к другому конструктору. Из-за такого поведения любое нарушение, возникающее в **анонимаусмесод** , должно быть подавлено отдельно. Это также означает, что если появился новый конструктор, то предупреждения, которые ранее были подавлены для **класса (int)** и **класса (String)** , также должны быть подавлены в новом конструкторе.

 Эту ошибку можно обойти одним из двух способов. Можно объявить **анонимаусмесод** в общем конструкторе, который является цепочкой всех конструкторов. Или можно объявить его в методе инициализации, который вызывается всеми конструкторами.

## <a name="see-also"></a>См. также раздел
 [Анализ качества управляемого кода](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
