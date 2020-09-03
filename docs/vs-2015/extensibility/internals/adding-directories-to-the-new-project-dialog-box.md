---
title: Добавление каталогов в диалоговое окно "новый проект" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8a9eeca4dc455c4f16e3551541454483138a993
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203876"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Добавление каталогов в диалоговое окно "Создание проекта"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При создании новых типов проектов можно также зарегистрировать новый каталог в диалоговом окне **Новый проект** , чтобы отобразить их для использования в качестве шаблонов. В следующем примере кода показано, как зарегистрировать новый каталог, также известный как узел. В этом примере регистрируются шаблоны, предоставляемые пакетом VSPackage CLSID_Package. В результате в левой части диалогового окна **Новый проект** появится добавленный узел с именем, определенным ресурсом Folder_Label_ResID. Этот ресурс загружается из вспомогательной библиотеки DLL VSPackage.  
  
 Значение **папки** представляет идентификатор GUID папки, в которой отображается узел Folder_Label_ResID. В этом примере идентификатор GUID представляет папку **другие проекты** на панели **типы проектов** диалогового окна **Новый проект** . Если значение **других проектов** отсутствует, метка располагается на верхнем уровне.  
  
 Значение Темплатесдир указывает полный путь к каталогу, содержащему шаблоны проектов. Эти файлы могут представлять собой файлы. vsz или обычные файлы шаблонов для клонирования.  
  
 Если указать Темплатеслокализедсубдир, это должен быть идентификатор ресурса строки, которая содержит имя подкаталога Темплатесдир, содержащего локализованные шаблоны. Поскольку [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] загружает строковый ресурс из вспомогательной библиотеки DLL, если таковой имеется, каждая вспомогательная библиотека DLL может содержать другое имя подкаталога. Значение Сортприорити задает приоритет сортировки.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Добавление элементов в диалоговые окна "Добавление нового элемента"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Добавление каталогов в диалоговое окно "Добавить новый элемент"](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
