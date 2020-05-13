---
title: Настойчивость проекта Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10a9cde91c0181fbfefbaa353c7c3702f4b36819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706458"
---
# <a name="project-persistence"></a>Сохранение проекта
Настойчивость является ключевым проектным соображением для вашего проекта. В большинстве проектов используются элементы проекта, представляющие файлы; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] также поддерживает проекты, данные которых не основаны на файлах. Необходимо сохранить как файлы, принадлежащие проекту, так и файл проекта. IDE инструктирует проект, чтобы сохранить себя или элемент проекта.

 Шаблоны для проектов передаются на проектную фабрику. Шаблоны должны поддерживать инициализацию всех элементов проекта в соответствии с требованиями конкретного типа проекта. Эти шаблоны позже могут быть сохранены в виде файлов проектов и управляются IDE через решение. Для получения дополнительной информации [Solutions](../../extensibility/internals/solutions-overview.md)см. [Creating Project Instances By Using Project Factories](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Элементы проекта могут быть основаны на файлах или без файла:

- Элементы на основе файлов могут быть локальными или удаленными. Например, в веб-проектах в СЗ подключение к файлам удаленной системы сохраняется локально, в то время как сами файлы сохраняются в удаленной системе.

- Элементы, не основанные на файлах, могут сохранять элементы в базе данных или репозитории.

## <a name="commit-models"></a>Модели фиксации
 После определения места расположения элементов проекта необходимо выбрать соответствующую модель коммита. Например, в модели на основе файлов с локальными файлами каждый проект может быть сохранен автономно. В модели репозитория можно сохранить несколько элементов в одной транзакции. Для получения дополнительной [Project Type Design Decisions](../../extensibility/internals/project-type-design-decisions.md)информации см.

 Чтобы определить расширение названия файлов, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> проекты реализуют интерфейс, который предоставляет информацию, позволяющую клиенту объекта реализовать диалоговое поле **Save As,** то есть заполнить список выпадающих типов **Save As** type и управлять первоначальным расширением имени файла.

 IDE называет `IPersistFileFormat` интерфейс проекта, чтобы показать, что проект должен сохранять свои элементы проекта по мере необходимости. Таким образом, объект владеет всеми аспектами своего файла и формата. Это включает в себя название формата объекта.

 В случае, когда элементы `IPersistFileFormat` не являются файлами, по-прежнему сохраняется способ сохранения элементов, не связанных с файлами. Файлы проектов, такие как [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] файлы .vbp [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] для проектов или файлы .vcproj для проектов, также должны быть упорными.

 Для сохранения действия IDE изучает таблицу исходного документа (RDT), а <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> иерархия <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> передает команды и интерфейсы. Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> реализован для определения того, был ли элемент изменен. Если элемент имеет, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> метод реализован для сохранения измененного элемента.

 Методы интерфейса `IVsPersistHierarchyItem2` используются для определения того, можно ли перезагрузить элемент, и, если элемент может быть, перезагрузить его. Кроме того, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> метод может быть реализован, чтобы привести к отбрасыванию измененных элементов без сохранения.

## <a name="see-also"></a>См. также
- [Контрольный список. Создание типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Создание экземпляров проекта с помощью фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
