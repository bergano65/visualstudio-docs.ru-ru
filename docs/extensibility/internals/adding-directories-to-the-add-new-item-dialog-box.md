---
title: Добавление каталогов, чтобы добавить новый элемент-диалоговое окно | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 981b65df9354277580ee1c816f4e0fd0977f9a85
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328019"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Добавить каталоги в диалоговом окне Добавление нового элемента
В следующем примере кода показано, как зарегистрировать новый набор каталогов для **Добавление нового элемента** диалоговое окно. Каталоги для **Добавление нового элемента** диалоговое окно отличаются для каждого проекта. Таким образом, каталоги, зарегистрированные в разделе **проекты** подраздел, в **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.

## <a name="registry-script"></a>Скрипт реестра

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

 `%Template_Path%` Значение указывает полный путь к каталогу, содержащему шаблоны проектов. Эти шаблоны могут быть либо *.vsz* файлы или файлы описания шаблонов для клонирования.

 `SortPriority` Значение указывает приоритет сортировки.

## <a name="add-items-to-an-existing-project"></a>Добавление элементов в существующий проект
 Можно также добавить элементы в существующий проект. Например, для [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] проекта, можно добавить элементы к  *\<корневой > \Program Files\Microsoft Visual Studio\VC#\CSharpProjectItems\LocalProjectItems* папки. В этом случае `%GUID_Project%` – идентификатор GUID для проекта C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Также можно расширить существующий проект запрограммировав подтипа проекта. Подтип проекта вы можете расширить проект без написания нового типа проекта. Дополнительные сведения о подтипов проекта, см. в разделе [подтипы проекта](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>См. также
- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)
- [Добавление элементов в диалоговом окне Добавление нового элемента](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Добавить каталоги в диалоговое окно нового проекта](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)