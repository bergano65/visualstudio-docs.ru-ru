---
title: Элементы модели проекта (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf847e35878dc84bb32fe81053c01c23e565fc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708525"
---
# <a name="elements-of-a-project-model"></a>Элементы модели проекта
Интерфейсы и реализации всех [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проектов в общей сложности базовая структура: модель проекта для вашего типа проекта. В вашей модели проекта, которая является VSPackage вы разрабатываете, вы создаете объекты, которые соответствуют вашим дизайнерским решениям и работать вместе с глобальной функциональности, предоставляемой IDE. Хотя, например, вы контролируете сохранение элемента проекта, вы не контролируете уведомление о том, что файл должен сохраняться. Когда пользователь уделяет основное внимание элементу открытого проекта и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] выбирает **сохранить** в меню **файла** в панели меню, код типа проекта должен перехватить команду из IDE, сохранить файл и отправить уведомление обратно в IDE, что файл больше не изменяется.

 Ваш VSPackage взаимодействует с IDE через службы, предоставляющие доступ к интерфейсам IDE. Например, с помощью определенных служб вы отслеживаете и маршрутируете команды и предоставляете контекстную информацию для выбора, сделанного в проекте. Вся глобальная функциональность IDE, необходимая для вашего VSPackage, предоставляется услугами. Для получения дополнительной информации об услугах [см.](../../extensibility/how-to-get-a-service.md)

 Другие соображения реализации:

- Одна модель проекта может содержать несколько типов проектов.

- Типы проектов и сопутствующие проектные фабрики регистрируются независимо с ПОМОЩЬю GUID.

- Каждый проект должен иметь файл шаблона или мастера для инициализации [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] нового файла проекта, когда пользователь создает новый проект через пользовательский интерфейс. Например, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] шаблоны инициализируют то, что в конечном итоге станет файлами .vcproj.

  На следующей иллюстрации показаны основные интерфейсы, службы и объекты, которые составляют типичную реализацию проекта. Вы можете использовать приложение `HierUtil7`помощник, для создания основных объектов и других шаблонов программирования. Для получения более `HierUtil7` подробной информации о помощнике приложения [см.](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)

  ![Visual Studio проект модели графических](../../extensibility/internals/media/vsprojectmodel.gif "vsПроектМодель") Модель проекта

  Для получения дополнительной информации о интерфейсах и службах, перечисленных в предыдущей диаграмме, и других дополнительных интерфейсах, не включенных в диаграмму, [см.](../../extensibility/internals/project-model-core-components.md)

  Проекты могут поддерживать команды и <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> поэтому должны реализовать интерфейс для участия в командной реукторе через GUID контекста команды.

## <a name="see-also"></a>См. также
- [Контрольный список: Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Для реализации типа проекта (СЗ) используйте классы проектов HierUtil7](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Основные компоненты проектной модели](../../extensibility/internals/project-model-core-components.md)
- [Создание экземпляров проектов с помощью проектных фабрик](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Как: Получить услугу](../../extensibility/how-to-get-a-service.md)
- [Создание типов проектов](../../extensibility/internals/creating-project-types.md)
