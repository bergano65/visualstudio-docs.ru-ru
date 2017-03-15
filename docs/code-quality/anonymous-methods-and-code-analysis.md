---
title: "Анонимные методы и анализ кода | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "анонимные методы, анализ кода"
  - "анализ кода, анонимные методы"
  - "методы, анонимные"
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# Анонимные методы и анализ кода
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Анонимным методом* называется метод, не имеющий имени.  Анонимные методы чаще всего используются для передачи блока кода в качестве параметра делегата.  
  
 В данном разделе описывается порядок обработки анонимных методов и метрик, связанных с анонимными методами, при анализе кода.  
  
## Анонимные методы, объявленные внутри члена  
 Предупреждения и метрики для анонимного метода, объявленного в члене, например в методе или методе доступа, связываются с членом, который данный метод объявляет.  Они не связываются с членом, который вызывает метод.  
  
 Например, в следующем классе все предупреждения, найденные в объявлении анонимного метода **anonymousMethod**, должны вызываться по отношению к методу **Method1**, а не методу **Method2**.  
  
```vb#  
  
        Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As  Integer) value > 5  
        Method2(anonymousMethod)  
    End Sub Sub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End Sub End Class  
```  
  
```c#  
  
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
  
## Встроенные анонимные методы  
 Предупреждения и метрики для анонимного метода, который объявлен как встроенное назначение полю, связываются с конструктором.  Если поле объявлено как `static` \(`Shared` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\), в таком случае предупреждения и метрики связываются с конструктором класса; в обратном случае они связываются с конструктором экземпляра.  
  
 Например, в следующем классе все предупреждения, найденные в объявлении анонимного метода **anonymousMethod1**, будут вызываться по отношению к неявно созданному используемому по умолчанию конструктору класса **Class**.  Тогда как все предупреждения, найденные внутри анонимного метода **anonymousMethod2**, будут применяться по отношению к неявно созданному конструктору класса.  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As     Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As      Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End Sub End Class  
```  
  
```c#  
  
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
  
 Класс может содержать встроенный анонимный метод, присваивающий значение полю с несколькими конструкторами.  В данном случае предупреждения и метрики связываются со всеми конструкторами, если конструктор не связан последовательно с другим конструктором в этом же классе.  
  
 Например, в следующем классе все предупреждения, найденные в объявлении анонимного метода **anonymousMethod**, должны вызываться по отношению к классам **Class\(int\)** и **Class\(string\)**, а не к классу **Class\(\)**.  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
Sub New()  
    New(CStr(Nothing))  
End Sub Sub New(ByVal a As Integer)  
End Sub Sub New(ByVal a As String)  
End Sub End Class  
```  
  
```c#  
  
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
  
 Несмотря на кажущуюся неожиданность, это происходит потому, что компилятор создает уникальный метод для каждого конструктора, не связанного последовательно с другим конструктором.  Из\-за такого порядка работы все нарушения, происходящие внутри анонимного метода **anonymousMethod**, необходимо подавлять отдельно.  Это также означает, что при добавлении нового конструктора предупреждения, которые до этого подавлялись по отношению к классам **Class\(int\)** и **Class\(string\)**, будет также необходимо подавлять по отношению к новому классу.  
  
 Данную проблему можно обойти одним из двух способов.  Можно объявить анонимный метод **anonymousMethod** в общем конструкторе, с которым последовательно соединены все конструкторы.  Или же можно объявить данный анонимный метод в методе инициализации, вызываемом всеми конструкторами.  
  
## См. также  
 [Анализ качества управляемого кода](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)