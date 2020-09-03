---
title: Добавление каталогов в диалоговое окно "Добавление нового элемента" | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d4af79f95c87271e9a10eece6c728daa9a81305
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710255"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Добавление каталогов в диалоговое окно "Добавление нового элемента"
В следующем примере кода показано, как зарегистрировать новый набор каталогов для диалогового окна " **Добавление нового элемента** ". Каталоги для диалогового окна « **Добавление нового элемента** » для каждого проекта различаются. Поэтому каталоги регистрируются в подразделе " **проекты** ", который находится в **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0exp\projects**.

## <a name="registry-script"></a>Сценарий реестра

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

 `%Template_Path%`Значение указывает полный путь к каталогу, содержащему шаблоны проектов. Эти шаблоны могут представлять собой файлы *. vsz* или файлы шаблонов прототипные для клонирования.

 `SortPriority`Значение указывает приоритет сортировки.

## <a name="add-items-to-an-existing-project"></a>Добавление элементов в существующий проект
 Кроме того, можно добавлять элементы в существующий проект. Например, для [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] проекта можно добавить элементы в папку * \<root> \Program Files\Microsoft Visual студио\вк # \кшарппрожектитемс\локалпрожектитемс* . В этом случае `%GUID_Project%` — это идентификатор GUID для проекта C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Можно также расширить существующий проект путем программирования подтипа проекта. С помощью подтипа проекта можно расширить проект, не написав новый тип проекта. Дополнительные сведения о подтипах проектов см. в разделе [Project подтипы](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>См. также раздел
- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)
- [Добавление элементов в диалоговое окно "Добавление нового элемента"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Добавление каталогов в диалоговое окно "новый проект"](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
