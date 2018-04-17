---
title: Проект сохраняемости | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b85bb6155ca25abec67b582dc4d877dbd8290501
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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