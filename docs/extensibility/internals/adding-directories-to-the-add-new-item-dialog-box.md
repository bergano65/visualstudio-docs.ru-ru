---
title: Добавление каталогов, чтобы добавить новый элемент-диалоговое окно | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b8d9989e8cf4ec8f0eb714a26e73d89fba339b71
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Добавление каталогов, чтобы добавить новый элемент-диалоговое окно
В следующем примере кода показано, как зарегистрировать новый набор каталогов для **Добавление нового элемента** диалоговое окно. Каталоги для **Добавление нового элемента** диалоговое окно различны для каждого проекта. Таким образом, зарегистрированных в подразделе проекты в каталоги \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
## <a name="the-registry-script"></a>Скрипт реестра  
  
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
  
 Значение Template_Path указывает полный путь каталога, который содержит шаблоны проектов. Эти шаблоны могут быть VSZ-файлы или файлы описания шаблонов для клонирования.  
  
 Значение SortPriority указывает приоритет сортировки.  
  
## <a name="adding-items-to-an-existing-project"></a>Добавление элементов к существующему проекту  
 Элементы можно также добавлять к существующему проекту. Например, для [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] проекта, можно добавить элементы в \<корневой > Папка \VC#\CSharpProjectItems\LocalProjectItems \Program Files\Microsoft Visual Studio. В этом случае `%GUID_Project%` — это GUID для проекта C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Кроме того, можно расширить существующий проект запрограммировав подтипом проекта. С подтипом проекта вы можете расширить проекта без написания новый тип проекта. Дополнительные сведения о подтипы проекта см. в разделе [подтипы проекта](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>См. также  
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Добавление элементов, чтобы добавить новый элемент диалоговые окна](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Добавление каталогов в диалоговое окно "Создание проекта"](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)