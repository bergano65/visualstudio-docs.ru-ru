---
title: Поддержка системы управления версиями | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ae3590a5d02c2b3f1d4b67f724d0177f671f7d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130693"
---
# <a name="supporting-source-control"></a>Поддержка системы управления версиями
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поддерживает извлечение файлов с сервера, возвраты и другие операции управления версиями для проекта или редактора. Как клиент системы управления версиями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предназначен для взаимодействия с помощью пакета управления версиями, такие как [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], который предоставляет архивирования, управление версиями и средства управления динамически определяемым набором файлов.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Модель для пакетов системы управления версиями](../../extensibility/internals/model-for-source-control-packages.md)  
 Описываются интерфейсы, необходимо реализовать тип проекта для поддержки системы управления версиями.  
  
 [Проектные решения](../../extensibility/internals/source-control-design-decisions.md)  
 Предоставляет вопросы, ответы изменения, как реализовать тип проекта.  
  
 [Сведения о конфигурации](../../extensibility/internals/source-control-configuration-details.md)  
 Описывает, как поддержка системы управления версиями изменяется реализацию данного типа проекта.  
  
 [Дополнительные рекомендации для проектов и редакторы](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Описывает рекомендации по типам проектов и редакторов.  
  
 [Сведения о времени выполнения](../../extensibility/internals/source-control-runtime-details.md)  
 Описывает, как зарегистрировать проекта, когда пользователь добавляет его в систему управления версиями.  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Указывает среду или исходного пакета управления, предназначенное для изменения в памяти или сохранить файл.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Позволяет проекты и иерархии регистрирует себя с помощью системы управления версиями и получать сведения о состояние системы управления версиями.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Реализован в системе проектов для обеспечения системы управления версиями файлы проекта и элементов проекта.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Используется в проектах, чтобы запросить среду для разрешения на добавление, удаление или переименование файла или каталога в решении.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Сообщает клиенту об изменениях, внесенных в проект файлы или каталоги.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Общие сведения о проектах как основных стандартных блоках [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE). Приводятся ссылки на дополнительные разделы, в которых объясняется, как проекты контролировать создание и компиляция кода.