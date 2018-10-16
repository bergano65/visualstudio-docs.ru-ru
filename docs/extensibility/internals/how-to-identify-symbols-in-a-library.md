---
title: 'Практическое: определение символов в библиотеке | Документация Майкрософт'
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
ms.openlocfilehash: 7ff3f9ad93ddfb3b463d059fb2aba654ce48a501
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510533"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Практическое: определение символов в библиотеке
Средства просмотра символов отображения иерархических представлений символов. Символы представляют пространств имен, объекты, классы, члены класса и остальных элементов языка.  
  
 Каждый символ в иерархии можно определить по навигации, передаваемого в библиотеку символов для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчера объектов через следующие интерфейсы:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 Расположение символа в иерархии, являющийся отличительным признаком символа. Она позволяет средства просмотра символов для перехода к специальный символ. Уникальный, полный путь к символ определяет расположение. Каждый элемент в пути является узлом. Путь начинается с узла верхнего уровня и заканчивается специальный символ. Например если C1 — в пространстве имен N1 M1 метод является элементом класса C1, полный путь к метод M1 является N1. C1. M1. Этот путь содержит три узла: N1, C1 и M1.  
  
 Сведения о навигации позволяет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчера объектов, найдите и выберите Сохранить выбранные символы в иерархии. Она позволяет переход из одного средства просмотра. При использовании **обозреватель объектов** для просмотра символов в [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] проекта, можно правой кнопкой мыши метод и начать **Обозреватель вызовов** средство для отображения в графе вызовов метода.  
  
 Две формы описания расположения символов. Каноническая форма основан на полное имя пути символа. Оно представляет уникальный позицию символа в иерархии. Он не зависит от средства просмотра символов. Для получения сведений канонической форме, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] manager вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> метод. Форма представления описывает расположение символа в пределах определенного инструмента просмотра символов. Положение символа является относительно положения других символов в иерархии. Данный символ может иметь несколько путей презентации, но только один канонический путь. Например, если класс C1 наследуется от класса C2 и оба класса находятся в пространстве имен N1 **обозреватель объектов** иерархическое дерево:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Канонический путь к классу C2, в этом примере используется N1 + C2. Путь к презентации C2 включает в себя узлы C1 и «Базовых классов и интерфейсов»: N1 + C1 + «Базовых классов и интерфейсов» + C2.  
  
 Для получения информации из формы представления, диспетчер объектов вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> метод.  
  
  
## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Для получения канонические и презентации forms сведения  
  
1.  Выполните метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.  
  
     Диспетчер объектов вызывает этот метод для получения списка узлов, содержащихся по каноническому пути символа.  
  
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
  
     Диспетчер объектов вызывает этот метод для получения списка узлов, содержащихся по презентационному пути символа.  
  
## <a name="see-also"></a>См. также  
 [Поддержка средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Практическое: зарегистрировать библиотеку с диспетчером объектов](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Практическое: предоставлять список символов, предоставляемые библиотекой в диспетчер объектов](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)