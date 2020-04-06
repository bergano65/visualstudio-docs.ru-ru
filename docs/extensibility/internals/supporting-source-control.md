---
title: Поддержка управления источниками (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84de3120783528d209b1475477aee5087edac42b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704729"
---
# <a name="supporting-source-control"></a>Поддержка системы управления версиями
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]поддерживает проверки файлов, регистрацию и другие операции управления исходным источником для вашего проекта или редактора. Как клиент управления [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] исходным источником, предназначен для взаимодействия [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]с пакетом управления исходным источником, таким как , который обеспечивает архивирование, версия и управление средствами для динамически определенного набора файлов.

## <a name="in-this-section"></a>В этом разделе
- [Модель для пакетов системы управления версиями](../../extensibility/internals/model-for-source-control-packages.md)

 Описывает интерфейсы, которые должен быть реализован тип проекта для поддержки управления исходным ресурсом.

- [Проектные решения](../../extensibility/internals/source-control-design-decisions.md)

 Предоставляет вопросы, ответы на которые изменяют способ реализации типа проекта.

- [Подробная информация о конфигурации](../../extensibility/internals/source-control-configuration-details.md)

 Описывает, как поддержка управления исходным источником изменяет реализацию типа проекта.

- [Дополнительные рекомендации для проектов и редакторов](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Обсуждает лучшие практики для типов проектов и редакторов.

- [Сведения о среде выполнения](../../extensibility/internals/source-control-runtime-details.md)

 Описывает, как зарегистрировать проект, когда пользователь добавляет его в систему управления исходным элементом.

## <a name="reference"></a>Справочник
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>Указывает на пакет управления средой или исходным ресурсом, что файл вот-вот будет изменен в памяти или сохранен.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>Позволяет проектам и иерархиям зарегистрироваться с помощью управления исходным ресурсом и получить информацию о состоянии управления исходным источником.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>Реализована в проектной системе для обеспечения управления исходным элементом для файлов проектов и элементов проекта.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>Используется проектами для запроса среды для получения разрешения на добавление, удаление или переименование файла или каталога в решении.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>Уведомляет клиентов об изменениях, внесенных в файлы или каталоги проектов.

## <a name="related-sections"></a>Связанные разделы
- [Типы проектов](../../extensibility/internals/project-types.md)

 Обеспечивает обзор проектов в качестве основных [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] строительных блоков интегрированной среды разработки (IDE). Ссылки предоставляются на дополнительные темы, объясняющие, как проекты контролируют строительство и компиляцию кода.
