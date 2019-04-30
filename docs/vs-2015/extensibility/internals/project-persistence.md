---
title: Проект сохраняемости | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: abbcc1fc1048866ef790a4b6779ed15ef80a9be1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62429526"
---
# <a name="project-persistence"></a>Сохранение проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Основные проектные сохраняемости важно для вашего проекта. Большинство проектов использовать элементы проектов, которые представляют файлы; [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] также поддерживает проекты, данные, не являющиеся файловыми. Должны сохраняться файлы, принадлежащие проекта и файл проекта. Интегрированная среда разработки указывает, что проект, чтобы сохранить само себя или элемента проекта.  
  
 Шаблоны для проектов, передаются на фабрику проектов. Шаблоны должен поддерживать инициализацию всех элементов проекта в соответствии с требованиями проекта определенного типа. Позже эти шаблоны можно сохранить с файлами проекта и управляет интегрированной среды разработки через решение. Дополнительные сведения см. в разделе [создание экземпляров с помощью проекта фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) и [решения](../../extensibility/internals/solutions-overview.md).  
  
 Элементы проекта может быть копирование файла или не являющиеся файловыми:  
  
- Элементы на основе файлов может быть локальным или удаленным. Веб-проектов на C# например, подключения к файлам в удаленной системе сохранять локально, а сами файлы сохраняются в удаленной системе.  
  
- Элементы на основе файлов не может сохранять элементы в базе данных или хранилище.  
  
## <a name="commit-models"></a>Зафиксировать моделей  
 После того, где находятся элементы проекта, необходимо выбрать модель соответствующего подтверждения. Например в модели на основе файла с помощью локальных файлов каждого проекта можно сохранить автономно. В модели репозитория можно сохранить несколько элементов в одной транзакции. Дополнительные сведения см. в разделе [проектные решения проекта](../../extensibility/internals/project-type-design-decisions.md).  
  
 Для определения расширения имен файлов, реализовать проекты <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> интерфейс, который предоставляет сведения, позволяющие клиенту объекта требуется реализовать **Сохранить как** диалоговое окно — то есть для заполнения **тип**  выберите в раскрывающемся списке и управление ими расширение имени исходного файла.  
  
 Интегрированная среда разработки вызовы `IPersistFileFormat` интерфейс в проекте, чтобы указать, что проект должен сохранять его проект элементов соответствующим образом. Таким образом объект, которому принадлежит все аспекты его файл и формат. Это включает в себя имя формата объекта.  
  
 В случае, где элементы не являются файлами `IPersistFileFormat` по-прежнему как не являющиеся файловыми элементы сохраняются. Файлы, такие как файлы .vbp для проекта [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] файлы проектов или .vcproj [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] проектов, также должны быть неизменными.  
  
 Для сохранения действия, IDE проверяет таблице выполняющихся документов (RDT) и иерархии передает команды как <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> интерфейсов. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> Метод реализуется для определения, был ли изменен элемент. Если у элемента, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> метод реализуется для сохранения измененного элемента.  
  
 Методы в `IVsPersistHierarchyItem2` интерфейса используются для определения ли элемент может быть перезагружен, и если этот элемент может быть, перезагрузить его. Кроме того <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> метод может быть реализован для измененных элементов будет отброшен без сохранения.  
  
## <a name="see-also"></a>См. также  
 [Контрольный список. Создание типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Создание экземпляров проекта с помощью фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
