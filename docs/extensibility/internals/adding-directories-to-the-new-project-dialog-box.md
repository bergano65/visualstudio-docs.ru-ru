---
title: "Добавление папки в диалоговом окне Новый проект | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Диалоговое окно "новый проект", расширение"
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Добавление папки в диалоговом окне Новый проект
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

При создании новых типов проектов, можно зарегистрировать в новый каталог **Создать проект** диалоговое окно для отображения их для использования в качестве шаблонов.  В следующем примере кода показано, как зарегистрировать новый каталог, называемый также узел.  В этом примере зарегистрированных шаблонов, предоставляемые VSPackage CLSID\_Package.  В результате, left **Создать проект** диалоговое окно предлагает добавленный узел с именем, указанным ресурсом Folder\_Label\_ResID.  Этот ресурс загружен из вспомогательной библиотеке DLL VSPackage.  
  
 **папка** значение представляет идентификатор GUID папки, в которой отображается узел Folder\_Label\_ResID.  В примере идентификатор GUID, представляющее **другие проекты** в папку  **Типы проектов** панель   **Создать проект** диалоговое окно.  Если **другие проекты** значение отсутствует, метка располагается в верхнем уровне.  
  
 Значение TemplatesDir указывает полный путь к каталогу, содержащему шаблоны проектов.  Эти файлы могут быть либо файлы vsz или типичными файлы шаблона, который необходимо клонировать.  
  
 При указании TemplatesLocalizedSubDir, то должен быть идентификатором ресурса строки, что имена подкаталог TemplatesDir, содержащий локализовали шаблоны.  Поскольку [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загружает строковый ресурс из спутникового библиотеки DLL, если имеется одно, то каждое вспомогательной библиотеки DLL может содержать другое имя вложенного каталога. Значение SortPriority указывающее приоритет сортировки.  
  
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
  
## См. также  
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Добавление элементов, чтобы добавить новый элемент диалоговые окна](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Добавление каталогов, чтобы добавить новый элемент\-диалоговое окно](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)