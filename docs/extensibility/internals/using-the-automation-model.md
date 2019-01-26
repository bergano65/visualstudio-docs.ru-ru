---
title: С помощью модели автоматизации | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39c3de415e7c0c8f95380a76de7f8f8a717d97d4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015437"
---
# <a name="using-the-automation-model"></a>Использование модели автоматизации
После подключения VSPackage в службу автоматизации, можно получить свойства и методы, вызвав <xref:EnvDTE.DTEClass.GetObject%2A> метод <xref:EnvDTE._DTE> объекта, передав строку, представляющую объект, который нужно получить.  
  
## <a name="obtaining-project-objects"></a>Получение объектов проекта  
 Ниже приведены два примера кода, в которых показано, как потребитель автоматизации получает проект, объекты автоматизации. Сведения о том, как получить объект DTE см. в разделе [как: Получение ссылок на объекты DTE и DTE2](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
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
  
 На этом этапе можно использовать стандартный проект объекты, которые являются частью определенный пакет VSPackage, чтобы переместить вниз иерархическая модель.  
  
 В следующем примере кода показано, как получить пользовательского объекта, который является свойством пользовательского типа проекта.:  
  
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