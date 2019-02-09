---
title: Предупреждения при анализе кода анонимный метод
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a10c5baaed3a98e44d581b6ddb8d6e3a1883d079
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55940494"
---
# <a name="anonymous-methods-and-code-analysis"></a>Анонимные методы и анализ кода

*Анонимный метод* — это метод, который не имеет имени. Анонимные методы часто используются для передачи блока кода в качестве аргумента делегата. В этой статье объясняется, как анализ кода обрабатывает предупреждения и метрики для анонимных методов.

## <a name="anonymous-methods-declared-in-a-member"></a>Анонимные методы, объявленные в элементе

Предупреждения и метрики для анонимного метода, объявленного в члене, например, метод или метод доступа, связаны с членом, который объявляет метод. Они не связаны с членом, который вызывает метод.

Например, в следующем классе все предупреждения, которые находятся в объявлении **anonymousMethod** должен вызываться по отношению **Method1** и не **Method2**.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass
    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End Sub
    Sub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End Sub
End Class
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

Предупреждения и метрики для анонимного метода, объявленного как встроенное назначение полю связаны с конструктором. Если поле объявляется как `static` (`Shared` в Visual Basic), предупреждения и метрики, связанные с конструктором класса. В противном случае они связаны с конструктором экземпляра.

Например, в следующем классе все предупреждения, которые находятся в объявлении **anonymousMethod1** будет вызываться по отношению конструктор неявно создаваемый по умолчанию **класс**. Предупреждения, которые находятся в **анонимного метода anonymousMethod2** нужно применять конструктор неявно создаваемый класс.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass
    Dim anonymousMethod1 As ADelegate = Function(ByVal value As Integer) value > 5
    Shared anonymousMethod2 As ADelegate = Function(ByVal value As Integer) value > 5

    Sub Method1()
        anonymousMethod1(10)
        anonymousMethod2(10)
    End Sub
End Class
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

Например, в следующем классе все предупреждения, которые находятся в объявлении **anonymousMethod** должен вызываться по отношению **Class(int)** и **Class(string)**, но не для **Class()**.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass

    Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5

    SubNew()
        New(CStr(Nothing))
    End Sub

    Sub New(ByVal a As Integer)
    End Sub

    Sub New(ByVal a As String)
    End Sub
End Class
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

Предупреждения создаются для конструкторов, так как компилятор выводит уникальный метод для каждого конструктора, который не связан с другим конструктором. Из-за этого поведения, все нарушения, выполняемая в **anonymousMethod** должны подавляться отдельно. Это также означает, что если новый конструктор появился, предупреждения, которые ранее были скрыты от **Class(int)** и **Class(string)** должны подавляться для нового конструктора.

Можно обойти эту проблему в одном из двух способов:

- Объявите **anonymousMethod** в общем конструкторе, все цепочки конструкторов.
- Объявите **anonymousMethod** в методе инициализации, который вызывается конструкторами всех.

## <a name="see-also"></a>См. также

- [Анализ качества управляемого кода](../code-quality/code-analysis-for-managed-code-overview.md)