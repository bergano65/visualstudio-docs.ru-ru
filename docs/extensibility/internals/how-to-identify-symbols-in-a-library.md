---
title: 'Как: определение символов в библиотеке | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 310ba421120101ce545888bcf4c069ca454cf086
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136132"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Как: определение символов в библиотеке
Средства обзора символ отображение иерархических представлений символов. Символы представляют пространств имен, объекты, классы, члены класса и остальные элементы языка.  
  
 Каждый символ в иерархии, можно определить по передал библиотеки символов для данных навигации [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчера объектов через следующие интерфейсы:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 Расположение символа в иерархии, являющийся отличительным признаком символа. Она позволяет средства обзора символ для перехода к специальный символ. Уникальный, полный путь к символ определяет расположение. Каждый элемент в пути является узлом. Путь начинается с узла верхнего уровня и заканчивается специальный символ. Например если метод M1 является членом класса C1 и C1 — в пространстве имен N1, полный путь к метод M1 — N1. C1. M1. Этот путь содержит три узла: N1, C1 и M1.  
  
 Данные навигации позволяет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчера объектов для поиска, выбора и сохранить выбранные символы в иерархии. Она позволяет переход от одного средством просмотра. При использовании **обозревателя объектов** для просмотра символов в [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] проекта, можно правой кнопкой мыши метод и начать **обозревателя вызовов** средство для отображения в графе вызовов метода.  
  
 Две формы описания расположения символов. Каноническая форма основан на полный путь символа. Он представляет уникальный положение символа в иерархии. Она не зависит от средства просмотра символа. Для получения информации каноническая форма [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчер вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> метод. Представления формы описывает расположение символа в пределах определенного инструмента просматриваемого символа. Положение символа — относительно положения в hierarchicy других символов. Данный символ может иметь несколько путей презентации, но только один канонический путь. Например, если C1 класс наследуется от класса C2 и оба класса находятся в пространстве имен N1 **обозревателя объектов** иерархическое дерево:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Канонический путь класса C2, в этом примере — N1 + C2. Путь презентации C2 включает в себя узлы C1 и «Базовых классов и интерфейсов»: N1 + C1 + «Базовых классов и интерфейсов» + C2.  
  
 Для получения сведений формы представления, вызовов диспетчера объектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> метод.  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>Определение символа в иерархии  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>Для получения канонические и презентации формирует сведения  
  
1.  Выполните метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.  
  
     Диспетчер объектов вызывает этот метод, чтобы получить список узлов, содержащихся в канонический путь символа.  
  
    ```vb  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```csharp  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  Выполните метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.  
  
     Диспетчер объектов вызывает этот метод для получения списка узлов, находящиеся в пути представления символа.  
  
## <a name="see-also"></a>См. также  
 [Вспомогательные средства обзора символ](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Как: регистрации библиотеки с помощью диспетчера объектов](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Практическое руководство. Предоставление списка символов, переданных из библиотеки в диспетчер объектов](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)