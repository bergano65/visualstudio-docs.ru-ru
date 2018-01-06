---
title: "Добавление каталогов, чтобы добавить новый элемент-диалоговое окно | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 878c06e1965b5a96510df0e1b28175972546e227
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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