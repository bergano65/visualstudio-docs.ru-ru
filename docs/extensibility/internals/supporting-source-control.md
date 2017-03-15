---
title: "Поддержка системы управления версиями | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "исходный элемент управления [Visual Studio SDK], поддержка"
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Поддержка системы управления версиями
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поддерживает извлечение файла, возвратов и другие операции системы управления версиями для проектов или редактора.  В качестве клиента системы управления версиями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проектирования для взаимодействия с пакетом системы управления версиями, например  [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], предоставляющий сжатие, управление версиями, а также возможности динамического элемента управления для заданного набора файлов.  
  
## В этом подразделе  
 [Модель для пакетов управления версиями](../../extensibility/internals/model-for-source-control-packages.md)  
 Описывает интерфейсы тип проекта должен реализовать для поддержки системы управления версиями.  
  
 [Решения](../../extensibility/internals/source-control-design-decisions.md)  
 Предоставляет вопросы ответы которых изменяются в качестве реализации типа проекта.  
  
 [Сведения о конфигурации](../../extensibility/internals/source-control-configuration-details.md)  
 Описывает, как сохранении изменений системы управления версиями, реализация типа проекта.  
  
 [Дополнительные рекомендации по проектам и редакторы](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Описывает рекомендации по типам проектов и редакторов.  
  
 [Сведения о времени выполнения](../../extensibility/internals/source-control-runtime-details.md)  
 Описывает, как зарегистрировать проекта, когда пользователь добавляет его в системаа управления.  
  
## Ссылка  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Указывает на пакет среды или системы управления версиями, что файл должен быть изменен в память или сохранения.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Разрешает проектов и иерархии зарегистрироваться в системе управления версиями и получения сведений о состоянии системы управления версиями.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Реализуемый в системе проектов для предоставления системы управления версиями файлов проектов и элементов проектов.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Используется проектами запросить среду для разрешения добавить, удалить или переименовать файл или каталог в решении.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Уведомляет клиентов об изменениях, внесенных в проект файлы или каталоги.  
  
## Связанные подразделы  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Общие сведения о проектах как базовые шаблоны [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированная среда разработки \(ide\).  Ссылки на дополнительные разделы, в которых объясняется, как построение проектов, элементов управления и кода следует компилировать.