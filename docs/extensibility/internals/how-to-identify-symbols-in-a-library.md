---
title: Как определить символы в библиотеке Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe920fabd05a875b336467fbba16e4229fa9613
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708000"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Как определить символы в библиотеке
Инструменты просмотра символов отображают иерархические представления символов. Символы представляют пространства имен, объекты, классы, членов классов и другие языковые элементы.

 Каждый символ в иерархии может быть идентифицирован навигационной информацией, передаваемый библиотекой символов диспетчеру [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] объектов через следующие интерфейсы:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 Расположение символа в иерархии отличает символ. Это позволяет инструменты просмотра символов перемещаться к определенному символу. Уникальный, полностью квалифицированный путь к символу определяет местоположение. Каждый элемент пути является узлом. Путь начинается с узла верхнего уровня и заканчивается конкретным символом. Например, если метод M1 является членом класса C1, а C1 — в пространстве имен N1, полным способом метода M1 является N1. C1. M1. Этот путь содержит три узла: N1, C1 и M1.

 Навигационная информация позволяет диспетчеру объектов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] находить, выбирать и сохранять выбранные символы в иерархии. Это позволяет перемещаться от одного инструмента просмотра к другому. При использовании **Object Browser** [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] для просмотра символов в проекте можно нажать по праву и запустить инструмент **Call Browser** для отображения метода на графике вызова.

 Две формы описывают расположение символа. Каноническая форма основана на полностью квалифицированном пути символа. Он представляет собой уникальное положение символа в иерархии. Он не зависит от инструмента просмотра символов. Чтобы получить информацию о канонической форме, диспетчер [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] объекта вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> метод. Форма презентации описывает расположение символа в определенном инструменте просмотра символов. Положение символа относительно положения других символов в иерархии. Данный символ может иметь несколько путей представления, но только один канонический путь. Например, если класс C1 наследуется от класса C2 и оба класса находятся в пространстве имен N1, **объект браузер** отображает следующее иерархическое дерево:

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 Канонический путь класса C2, в данном примере, n1 и C2. Путь презентации C2 включает в себя c1 и "Базы и интерфейсы" узлы: N1 и C1 " Базы и интерфейсы"

 Чтобы получить информацию о форме <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> презентации, диспетчер объекта вызывает метод.

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Получение канонической и презентационных форм информации

1. Выполните метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.

     Диспетчер объекта называет этот метод для получения списка узлов, содержащихся в канонической траектории символа.

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

2. Выполните метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.

     Диспетчер объекта вызывает этот метод для получения списка узлов, содержащихся в пути представления символа.

## <a name="see-also"></a>См. также
- [Поддержка инструментов просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Как: Регистрация библиотеки у диспетчера объектов](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Как: Выставлять списки символов, предоставленных библиотекой диспетчеру объекта](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
