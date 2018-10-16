---
title: Анонимные методы и анализ кода
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e069976badeffbce04b2f245277426441d3df2f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31892707"
---
# <a name="anonymous-methods-and-code-analysis"></a>Анонимные методы и анализ кода
*Анонимного метода* — метод, который не имеет имени. Анонимные методы чаще всего используются для передачи блока кода в качестве аргумента делегата.

 В этом разделе объясняется, обработка и метрик, связанных с анонимных методов анализа кода.

## <a name="anonymous-methods-declared-in-a-member"></a>Анонимные методы, объявленные в элементе
 Предупреждения и метрики для анонимного метода, объявленного в элементы, например метод или метод доступа, связанные с членом, который объявляет метод. Они не связаны с элементом, который вызывает метод.

 Например, в следующем классе все предупреждения, которые находятся в объявлении **anonymousMethod** должен вызываться по отношению **метод1** и не **метод2**.

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
 Предупреждения и метрики для анонимного метода, который объявлен как встроенное назначение полю, связываются с конструктором. Если поле объявлено как `static` (`Shared` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), предупреждения и метрики, связанные с конструктором класса; в противном случае, они связаны с конструктором экземпляра.

 Например, в следующем классе все предупреждения, которые находятся в объявлении **anonymousMethod1** от неявно создаваемый по умолчанию, будет создано **класса**. Тогда как все предупреждения, найденные в **анонимного метода anonymousMethod2** нужно применять конструктор неявно созданного класса.

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

 Класс может содержать встроенный анонимный метод, присваивающий значение полю, которое имеет несколько конструкторов. В этом случае предупреждения и метрики, связанные с все конструкторы, если конструктор связан другого конструктора этого же класса.

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

 Несмотря на то, что это может показаться неожиданным, это происходит потому, что компилятор создает уникальный метод для каждого конструктора, не существует цепочки от другого конструктора. В связи с этим любые, нарушение в **anonymousMethod** необходимо подавлять отдельно. Это также означает, что если новый конструктор появились предупреждения, которые ранее были скрыты от **Class(int)** и **Class(string)** также должны подавляться к новому классу.

 Можно обойти эту проблему, одним из двух способов. Можно объявить **anonymousMethod** в общем конструкторе, все цепочки конструкторов. Или можно объявить в методе инициализации, вызываемом всеми конструкторами.

## <a name="see-also"></a>См. также
 [Анализ качества управляемого кода](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)