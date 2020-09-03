---
title: Добавление каталогов в диалоговое окно "Добавление нового элемента" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f370d208cb8f7aad88f806983983ccee9f584625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203928"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Добавление каталогов в диалоговое окно "Добавить новый элемент"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В следующем примере кода показано, как зарегистрировать новый набор каталогов для диалогового окна " **Добавление нового элемента** ". Каталоги для диалогового окна « **Добавление нового элемента** » для каждого проекта различаются. Поэтому каталоги регистрируются в подразделе "проекты", расположенном в \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects> :  
  
## <a name="the-registry-script"></a>Сценарий реестра  
  
```  
NoRemove Projects  
{  
  NoRemove %GUID_Project%  
  {  
    NoRemove AddItemTemplates  
    {  
      NoRemove TemplateDirs  
      {  
        ForceRemove %CLSID_Package%  
        {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
          {  
            val TemplatesDir = s '%Template_Path%'     
            val SortPriority = d 2000  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
 Значение Template_Path указывает полный путь к каталогу, содержащему шаблоны проектов. Эти шаблоны могут представлять собой файлы. vsz или файлы шаблонов прототипные для клонирования.  
  
 Значение Сортприорити задает приоритет сортировки.  
  
## <a name="adding-items-to-an-existing-project"></a>Добавление элементов в существующий проект  
 Кроме того, можно добавлять элементы в существующий проект. Например, для [!INCLUDE[csprcs](../../includes/csprcs-md.md)] проекта можно добавить элементы в \<root> папку \Program Files\Microsoft Visual Studio \Вк # \кшарппрожектитемс\локалпрожектитемс. В этом случае `%GUID_Project%` является идентификатором GUID для проекта C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Можно также расширить существующий проект путем программирования подтипа проекта. С помощью подтипа проекта можно расширить проект, не написав новый тип проекта. Дополнительные сведения о подтипах проектов см. в разделе [Project подтипы](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>См. также:  
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Добавление элементов в диалоговые окна "Добавление нового элемента"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Добавление каталогов в диалоговое окно "Создание проекта"](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
