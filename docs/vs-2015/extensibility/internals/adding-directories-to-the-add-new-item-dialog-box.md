---
title: Добавление каталогов, чтобы добавить новый элемент-диалоговое окно | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a4623df5794ae29b97bbbdc077c465d822d6f4d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560048"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Добавление каталогов в диалоговое окно "Добавить новый элемент"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [добавления каталогов в диалоговое окно Добавить новый элемент](https://docs.microsoft.com/visualstudio/extensibility/internals/adding-directories-to-the-add-new-item-dialog-box).  
  
В следующем примере кода показано, как зарегистрировать новый набор каталогов для **Добавление нового элемента** диалоговое окно. Каталоги для **Добавление нового элемента** диалоговое окно отличаются для каждого проекта. Таким образом, зарегистрированных в подразделе Projects, в каталоги \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
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
  
 Значение Template_Path указывает полный путь к каталогу, содержащему шаблоны проектов. Эти шаблоны могут быть VSZ-файлы или файлы описания шаблонов для клонирования.  
  
 Значение SortPriority указывает приоритет сортировки.  
  
## <a name="adding-items-to-an-existing-project"></a>Добавление элементов в существующий проект  
 Можно также добавить элементы в существующий проект. Например, для [!INCLUDE[csprcs](../../includes/csprcs-md.md)] проекта, можно добавить элементы к \<корневой > Папка \VC#\CSharpProjectItems\LocalProjectItems \Program Files\Microsoft Visual Studio. В этом случае `%GUID_Project%` – идентификатор GUID для проекта C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Также можно расширить существующий проект запрограммировав подтипа проекта. Подтип проекта вы можете расширить проект без написания нового типа проекта. Дополнительные сведения о подтипов проекта, см. в разделе [подтипов проекта](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>См. также  
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Добавление элементов, чтобы добавить новый элемент диалоговые окна](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Добавление каталогов в диалоговое окно "Создание проекта"](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

