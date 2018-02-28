---
title: "С помощью модели автоматизации | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 525ed35f8d015661316bbd7d794cdcb246ba1e96
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-automation-model"></a>С помощью модели автоматизации
После подключения к автоматизации VSPackage, можно получить свойства и методы, вызвав <xref:EnvDTE.DTEClass.GetObject%2A> метод <xref:EnvDTE._DTE> объекта, передавая строка, представляющая объект, который нужно получить.  
  
## <a name="obtaining-project-objects"></a>Получение объектов проекта  
 Ниже приведены два примера кода, которые показывают, как потребитель автоматизации получает проекта объекты автоматизации. Сведения о том, как получить объект DTE см. в разделе [как: получение ссылки на DTE и DTE2 объектов](http://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
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
  
 На этом этапе можно использовать объекты для стандартного проекта, которые являются частью конкретных VSPackage для перемещения вниз в иерархии модели.  
  
 В следующем примере кода показано, как получить пользовательский объект, который является свойством пользовательского типа проектов.:  
  
```vb  
Dim MyPrj As Project  
Dim MyPrjItem As ProjectItem  
Dim objMyObject as MyExtendedObject  
  
MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project  
objMyObject = MyPrj.Object 'You call .Object to get to special Project  
                           'implementation  
objMyObject.MySpecialMethodOrProperty  
```  
  
 В следующем коде перечислены имена всех свойств в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды **Общие** параметр **средства** меню:  
  
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
 <xref:EnvDTE.DTEClass.GetObject%2A>