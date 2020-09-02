---
title: Использование модели автоматизации | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22ee836f5a4330c551181f01229e82eb14623fb8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675213"
---
# <a name="using-the-automation-model"></a>Использование модели автоматизации
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

После подключения VSPackage к службе автоматизации можно получить свойства и методы, вызвав <xref:EnvDTE.DTEClass.GetObject%2A> метод для <xref:EnvDTE._DTE> объекта, передав строку, представляющую объект, который вы хотите получить.  
  
## <a name="obtaining-project-objects"></a>Получение объектов проекта  
 Ниже приведены два примера кода, демонстрирующих, как потребитель автоматизации получает объекты автоматизации проекта. Сведения о том, как получить объект DTE, см. в разделе [инструкции. получение ссылок на объекты DTE и DTE2](https://msdn.microsoft.com/library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp#  
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
  
 В следующем коде перечислены имена всех свойств в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] параметре среда **Общие** в меню **Сервис** .  
  
```vb  
dim objDTE  
dim objEnv  
set objDTE = CreateObject("VisualStudio.DTE")  
set objEnv = objDTE.Properties("Environment", "General")  
for each obj in ObjEnv  
MsgBox obj.Name  
Next  
  
```  
  
## <a name="see-also"></a>См. также:  
 <xref:EnvDTE.DTEClass.GetObject%2A>
