---
title: "Практическое руководство: определение символов в библиотеке | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Средство обозревателя, определение символов в библиотеке"
  - "Средство обозревателя вызовов"
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Практическое руководство: определение символов в библиотеке
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Символ\-просмотреть иерархические представления отображения средств символов.  Символы, представляющие объекты пространства имен, классы, члены класса и другие элементы языка.  
  
 Каждый символ в иерархии может определяться данными о навигации передаваемых символов с библиотекой [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчер объекта через следующие интерфейсы:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 Положение символа в иерархии отличает символ.  Он позволяет символ\-просмотреть средства для перехода к определенному символу.  Уникальные полный путь к символу, указывающее местоположение.  Каждый элемент в пути узел.  Пути начинается с узлом верхнего уровня и заканчивается с определенным символом.  Например, если метод M1 член класса C1 и C1 в пространстве имен N1, то полный путь метода M1 N1.C1.M1.  Этот путь содержит 3 узла: N1, C1 и M1.  
  
 Сведения о навигации предоставляют [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчер объекта, который нужно найти, выбрав и сохранить выбрал символы в иерархии.  Она позволяет переходить от одного к другому. средства просмотра  При использовании **Обозреватель объектов** просмотр символов в выражении  [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] проект можно щелкнуть правой кнопкой мыши метод и начать  **Обозреватель вызовов** средство отображения диаграммы при вызове метода.  
  
 2 Формы описывается расположение символа.  Каноническая форма основана на полный путь к символам.  Она представляет уникальную положение символа в иерархии.  Это независимый символ\-просмотря средства.  Получить сведения о канонической формы <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> вызовы диспетчера объектов  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] метод.  Форма представления описывает расположение символа в указанное средство символ\-просмотря.  Позиция символа относительно позиции других символов в hierarchicy.  Заданный символ может иметь несколько путей представления, но только одного канонического пути.  Например, если класс наследуется от класса C1 и C2 оба класса в пространстве имен N1, **Обозреватель объектов** отображает иерархическое дерево следующее:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Канонического пути класса C2 в этом примере N1 \+ C2.  Путь представления включает узлы C1 и C2 "базовых объектов и интерфейсов": N1 \+ C1 \+ "базовые классы и интерфейсы" \+ C2.  
  
 Получить сведения о формы представления, вызовы диспетчера объектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> метод.  
  
## Указание символ в иерархии  
  
#### Получить сведения о канонических и представления с помощью форм  
  
1.  Реализуйте метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.  
  
     Диспетчер объекта вызывает этот метод для получения списка узлов, содержащихся в каноническом путь к символам.  
  
    ```vb#  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```c#  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  Реализуйте метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.  
  
     Диспетчер объекта вызывает этот метод для получения списка узлов, содержащихся в пути представления символа.  
  
## См. также  
 [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Практическое руководство: зарегистрировать библиотеку с помощью диспетчера объектов](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Практическое руководство: предоставлять список символов, предоставленный библиотекой диспетчера объектов](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)