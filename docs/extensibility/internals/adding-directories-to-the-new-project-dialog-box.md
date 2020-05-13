---
title: Добавление каталогов к новому проекту Dialog Box (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 827e383bba13c9742deb654bf3d680adeb3c109b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710245"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Добавление каталогов в диалоговую будку Нового проекта
При создании новых типов проектов можно также зарегистрировать новый каталог в диалоговом окне **нового проекта,** чтобы отобразить их для использования в качестве шаблонов. В следующем примере кода объясняется, как зарегистрировать новый каталог, также известный как узла. В примере регистрируются шаблоны VSPackage, *CLSID_Package.* В результате левая сторона диалогового окна **нового проекта** предлагает добавленный узла с именем, определяемым *Folder_Label_ResID* ресурсом. Этот ресурс загружается со спутника VSPackage DLL.

 Значение **Folder** представляет собой ГРАФИЧЕСКИй интерфейс папки, под которым отображается *Folder_Label_ResID* узла. В этом примере GUID представляет папку **«Другие проекты»** в панели **типа проекта** в диалоговом окне **нового проекта.** Если значение **Other Projects** отсутствует, метка расположена на верхнем уровне.

 Значение `TemplatesDir` определяет полный путь каталога, содержащего шаблоны проекта. Эти файлы могут быть либо *.vsz* файлы или типичные файлы шаблонов для клонирования.

 Если вы `TemplatesLocalizedSubDir`укажете, то это должен быть идентификатор ресурсов строки, которая называет субдиректор, который `TemplatesDir` содержит локализованные шаблоны. Поскольку [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ресурс строки загружается со спутника DLL, если он у вас есть, каждый спутник DLL может содержать другое название субдиректоров. Значение `SortPriority` определяет приоритет сортировки.

```
NoRemove NewProjectTemplates
{
    NoRemove TemplateDirs
  {
    ForceRemove %CLSID_Package%
    {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
      {
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'
        val TemplatesDir = s '%Template_Path%'
        val TemplatesLocalizedSubDir = s '#100'
        val SortPriority = d 1000
      }
    }
  }
}
```

## <a name="see-also"></a>См. также
- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)
- [Добавление элементов в диалоговую окно Добавить новый элемент](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Добавить каталоги в диалоговую коробку Добавить новый элемент](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
