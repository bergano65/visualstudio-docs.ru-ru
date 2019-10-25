---
title: Использование модели автоматизации | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f1e1479232a684758359de7527f0c2fc9990cc7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722096"
---
# <a name="using-the-automation-model"></a>Использование модели автоматизации
После подключения VSPackage к службе автоматизации можно получить свойства и методы, вызвав метод <xref:EnvDTE.DTEClass.GetObject%2A> для объекта <xref:EnvDTE._DTE>, передав строку, представляющую объект, который вы хотите извлечь.

## <a name="obtaining-project-objects"></a>Получение объектов проекта
 Ниже приведены два примера кода, демонстрирующих, как потребитель автоматизации получает объекты автоматизации проекта. Сведения о том, как получить объект DTE, см. в разделе [инструкции. получение ссылок на объекты DTE и DTE2](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).

```vb
Sub DoAutomation()
    Dim MyProjects As Projects
    MyProjects = DTE.GetObject("AcmeProject")
End Sub
```

```cpp
void DoAutomation(void)
{
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.
    pMyPkg = pDTE->GetObject("AcmeProjects");

   // The '=' performs a Query Interface.
   // Assumes pDTE is already available as a global.
   // Use pMyPkg to access your projects object's properties and methods.
}

```

 На этом этапе можно использовать стандартные объекты проекта, которые являются частью определенного VSPackage, чтобы переместить модель иерархии.

 В следующем примере кода показано, как получить пользовательский объект, являющийся свойством пользовательского типа проекта.

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 В следующем коде перечислены имена всех свойств в параметре [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды **Общие** в меню **Сервис** .

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>См. также
- <xref:EnvDTE.DTEClass.GetObject%2A>