---
title: Добавление каталогов в диалоговое окно нового проекта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26fe254a168ae1834fba804ca34d4e48bd240ca6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54941100"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Добавить каталоги в диалоговое окно нового проекта
При создании новых типов проектов, вы также можете зарегистрировать новый каталог в **новый проект** диалоговое окно, чтобы отобразить их для использования в качестве шаблонов. В следующем примере объясняется, как зарегистрировать новый каталог, а также называется узлом. В примере шаблоны, предоставляемые в пакете VSPackage, *CLSID_Package*, регистрируются. В результате в левой части **новый проект** диалоговое окно предлагает добавленный узел с именем определяется *Folder_Label_ResID* ресурсов. Этот ресурс загружается из вспомогательной Библиотеки VSPackage.  
  
 **Папку** значение представляет GUID папки, в которую *Folder_Label_ResID* узел отображается. В примере, представляет идентификатор GUID **другие проекты** папку в **типы проектов** области **новый проект** диалоговое окно. Если **другие проекты** значение отсутствует, то она позиционируется на верхнем уровне.  
  
 `TemplatesDir` Значение указывает полный путь к каталогу, содержащему шаблоны проектов. Эти файлы могут быть либо *.vsz* файлы или файлы типичный шаблон для клонирования.  
  
 Если указать `TemplatesLocalizedSubDir`, он должен быть идентификатор ресурса строки с именем в подкаталог `TemplatesDir` , содержащий локализованных шаблонов. Так как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загружает строковый ресурс из вспомогательной библиотеки DLL при наличии, каждой вспомогательной библиотеки DLL могут содержать разные подкаталог с именем. `SortPriority` Значение указывает приоритет сортировки.  
  
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
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Добавление элементов в диалоговом окне Добавление нового элемента](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Добавить каталоги в диалоговом окне Добавление нового элемента](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)