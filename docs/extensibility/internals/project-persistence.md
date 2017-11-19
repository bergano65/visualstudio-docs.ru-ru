---
title: "Проект сохраняемости | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7bb782b79c00576a431c8f4453ddf020606aaf5a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="project-persistence"></a>Долговременного хранения проекта
Ключевые особенности сохраняемости важно для проекта. Большинство проектов использовать элементы проекта, которые представляют файлы; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] также поддерживает проекты, данные которого не под управлением файла. Файлы, принадлежащие проекта и файл проекта должен быть сохранен. Интегрированной среды разработки указывает, что проект для сохранения само себя или элемент проекта.  
  
 Шаблоны проектов, передаются в фабрики проектов. Шаблоны должен поддерживать инициализацию всех элементов проекта в соответствии с требованиями проекта определенного типа. Эти шаблоны можно позже сохраняются в виде файлов проекта и управляется интегрированной средой разработки через решения. Дополнительные сведения см. в разделе [Создание проекта экземпляров, с помощью проекта фабрик](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) и [решения](../../extensibility/internals/solutions.md).  
  
 Элементы проекта может быть файла или не под управлением файла:  
  
-   Элементы на основе файлов может быть локальным или удаленным. Веб-проекты в C# например, подключения к файлам на удаленной системе сохранять локально, в то время как сами файлы сохраняются на удаленном компьютере.  
  
-   Элементы на основе Non файл можно сохранить элементы в базе данных или хранилище.  
  
## <a name="commit-models"></a>Зафиксировать моделей  
 После того, где находятся элементы проекта, необходимо выбрать соответствующий фиксации модели. Например в модели на основе файла с локальными файлами каждого проекта можно сохранить автономно. В модели хранилища можно сохранить несколько элементов в одной транзакции. Дополнительные сведения см. в разделе [проектные решения проекта типа](../../extensibility/internals/project-type-design-decisions.md).  
  
 Для определения расширений имен файлов, реализовывать проекты <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> интерфейс, который предоставляет сведения, позволяя клиенту реализовать объект **Сохранить как** диалоговое окно — то есть, для заполнения **тип файла**  -раскрывающийся список и управление ими расширение имени исходного файла.  
  
 Интегрированная среда разработки вызовы `IPersistFileFormat` интерфейс в проекте для указания сохранение проекта его проект элементов соответствующим образом. Таким образом объект, которому принадлежит все аспекты его файл и формат. Это включает имя формата объекта.  
  
 В случае, когда элементы не являются файлами `IPersistFileFormat` по-прежнему как файл использующего элементы сохраняются. Файлы, например .vbp файлы для проекта [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] проектов или .vcproj файлы для [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] проекты, также должен быть сохранен.  
  
 Для сохранения действия, IDE проверяет запуска таблицы документов (RDT) и иерархии передает команды <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> интерфейсов. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> Метод реализуется для определения, был ли изменен элемент. Если элемент имеет, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> метод реализуется для сохранения измененного элемента.  
  
 Методы в `IVsPersistHierarchyItem2` интерфейса используются для определения элемента можно загрузить в память и, если элемент можно перезагрузить его. Кроме того <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> метод может быть реализован для измененных элементов будут отменены без сохранения.  
  
## <a name="see-also"></a>См. также  
 [Контрольный список: Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Создание экземпляров проекта с помощью фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)