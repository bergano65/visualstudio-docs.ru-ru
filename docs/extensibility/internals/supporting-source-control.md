---
title: Поддержка системы управления версиями | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35fb66927272435e773dbaee44019103892b028d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62858084"
---
# <a name="supporting-source-control"></a>Поддержка системы управления версиями
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поддерживает извлечение файлов с сервера, возвраты и другие операции управления версиями для проекта или редактора. Как клиент системы управления версиями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предназначен для взаимодействия с помощью пакета системы управления версиями, такие как [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], который предоставляет архивации, управление версиями и средства управления динамически определяемым набором файлов.

## <a name="in-this-section"></a>В этом разделе
- [Модель для пакетов системы управления версиями](../../extensibility/internals/model-for-source-control-packages.md)

 Описываются интерфейсы, должен реализовывать тип проекта для поддержки системы управления версиями.

- [Проектные решения](../../extensibility/internals/source-control-design-decisions.md)

 Содержит вопросы, ответы на изменение, как реализовать тип проекта.

- [Подробные данные конфигурации](../../extensibility/internals/source-control-configuration-details.md)

 Описывает, как поддержка системы управления версиями изменяет реализацию типа проекта.

- [Дополнительные рекомендации для проектов и редакторов](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Рекомендации по типам проектов и редакторов.

- [Сведения о среде выполнения](../../extensibility/internals/source-control-runtime-details.md)

 В этой статье описывается регистрация проекта, когда пользователь добавляет его в систему управления версиями.

## <a name="reference"></a>Ссылка
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> Указывает среду или пакет системы управления версиями, что файл будет изменен в памяти или сохранен.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> Позволяет проектов и иерархий регистрирует себя с помощью системы управления версиями и получать сведения о состояния системы управления версиями.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> Реализован в системе проектов для обеспечения системы управления версиями файлы проекта и элементов проекта.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Используется проектами для запроса у среды разрешения добавить, удалить или переименовать файл или каталог в решении.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> Уведомляет клиентов об изменениях, внесенных в проект файлы или каталоги.

## <a name="related-sections"></a>Связанные разделы
- [Типы проектов](../../extensibility/internals/project-types.md)

 Общие сведения о проектах как основные стандартные блоки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE). Приведены ссылки на дополнительные разделы, в которых объясняется, как управлять проектами, создания и компиляции кода.