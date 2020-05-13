---
title: Добавление каталогов в добавленный новый пункт Диалог Box (ru) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710255"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Добавить каталоги в диалоговую коробку Добавить новый элемент
Следующий пример кода показывает, как зарегистрировать новый набор каталогов для диалогового окна **Add New Item.** Каталоги для диалогового окна **Добавить новый элемент** различны для каждого проекта. Таким образом, каталоги зарегистрированы в рамках подключаемых **проектов,** найденных в **HKEY_LOCAL_MACHINE»SOFTWARE-Microsoft-VisualStudio-8.0Exp ..**

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

 Значение `%Template_Path%` определяет полный путь каталога, содержащего шаблоны проекта. Эти шаблоны могут быть либо *.vsz* файлов или прототипных файлов шаблонов для клонирования.

 Значение `SortPriority` определяет приоритет сортировки.

## <a name="add-items-to-an-existing-project"></a>Добавление элементов в существующий проект
 Можно также добавить элементы в существующий проект. Например, для [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] проекта можно добавлять элементы в * \<корневую папку> »Файлы программы»-Microsoft Visual Studio»-CSharpProjectItems-LocalProjectItems.LocalProjectItems.* В данном `%GUID_Project%` случае, является GUID для проекта СЗ (FAE04EC0-301F-11D3-BF4B-00C04F79EF).

 Можно также расширить существующий проект, запрограммировав подтип проекта. С подтипом проекта можно расширить проект без написания нового типа проекта. Для получения дополнительной информации [Project subtypes](../../extensibility/internals/project-subtypes.md)о подтипах проектов см.

## <a name="see-also"></a>См. также
- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)
- [Добавление элементов в диалоговую окно Добавить новый элемент](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Добавление каталогов в диалоговую будку Нового проекта](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
