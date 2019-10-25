---
title: Сохраняемость проекта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a95c919de9b87ed1782cbdcb029efbf191958f5a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725463"
---
# <a name="project-persistence"></a>Сохранение проекта
Сохраняемость — это ключевой аспект разработки проекта. В большинстве проектов используются элементы проекта, представляющие файлы.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] также поддерживает проекты, данные которых не основаны на файлах. Файлы, принадлежащие проекту и файлу проекта, должны быть сохранены. Интегрированная среда разработки предписывает проекту сохранить себя или элемент проекта.

 Шаблоны для проектов передаются в фабрику проектов. Шаблоны должны поддерживать инициализацию всех элементов проекта в соответствии с требованиями конкретного типа проекта. Впоследствии эти шаблоны можно сохранить как файлы проекта и управлять ими с помощью интегрированной среды разработки. Дополнительные сведения см. в разделе [Создание экземпляров проектов с помощью фабрик](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) и [решений](../../extensibility/internals/solutions-overview.md)проекта.

 Элементы проекта могут иметь файловые или не основанные на файлах:

- Файловые элементы могут быть локальными или удаленными. В веб-проектах C#в, например, подключения к файлам в удаленной системе сохраняются локально, а сами файлы сохраняются в удаленной системе.

- Элементы, не являющиеся файлами на основе файлов, могут сохранять элементы в базе данных или репозитории.

## <a name="commit-models"></a>Фиксация моделей
 После выбора места расположения элементов проекта необходимо выбрать соответствующую модель фиксации. Например, в модели на основе файлов с локальными файлами каждый проект можно сохранить автономно. В модели репозитория можно сохранить несколько элементов в одной транзакции. Дополнительные сведения см. в разделе [решения по проектированию типов проектов](../../extensibility/internals/project-type-design-decisions.md).

 Чтобы определить расширения имен файлов, проекты реализуют интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>, который предоставляет сведения, позволяющие клиенту объекта реализовать диалоговое окно « **Сохранить как** », то есть для заполнения раскрывающегося списка « **Сохранить как тип** » и управления исходное расширение имени файла.

 Интегрированная среда разработки вызывает интерфейс `IPersistFileFormat` в проекте, чтобы указать, что проект должен сохранять свои элементы проекта соответствующим образом. Таким образом, объект владеет всеми аспектами его файла и формата. Сюда входит имя формата объекта.

 В случае, когда элементы не являются файлами, `IPersistFileFormat` продолжает сохранять нефайловые элементы. Файлы проекта, такие как vbp Files для [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] проектов или VCPROJ для проектов [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], также должны быть сохранены.

 Для действий сохранения интегрированная среда разработки проверяет таблицу выполняемых документов (РДТ), а иерархия передает команды <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> и интерфейсам <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>. Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> реализуется, чтобы определить, был ли изменен элемент. Если элемент имеет значение, метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> реализуется для сохранения измененного элемента.

 Методы в интерфейсе `IVsPersistHierarchyItem2` используются, чтобы определить, можно ли перезагрузить элемент, и, если элемент может быть, для его перезагрузки. Кроме того, метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> может быть реализован для того, чтобы измененные элементы были удалены без сохранения.

## <a name="see-also"></a>См. также
- [Контрольный список. Создание типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Создание экземпляров проекта с помощью фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)