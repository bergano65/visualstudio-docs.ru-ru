---
title: "Дополнение к модели автоматизации | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bb69380913f188031c97b46530ea2659fc05fe30
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="contributing-to-the-automation-model"></a>Contributing to the Automation Model
Visual Studio предоставляет набор интерфейсов автоматизации для настройки среды. Модель автоматизации — объектную модель, которая позволяет пользователям создавать надстройки Visual Studio и расширения.  
  
 Кроме того это решение подходит для вас, как разработчик VSPackage принять участие в модели автоматизации. Таким образом, включите конечные пользователи вашего VSPackage для создания надстроек и обычно целостное модели взаимодействие с пользователем при использовании VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Чтобы согласовать конечных пользователей, которые возникают, можно выполнить набор рекомендаций по при разработке пакета VSPackage, чтобы модель автоматизации для VSPackage следует идеи в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>В этом разделе  
 [Общие сведения о модели автоматизации](../../extensibility/internals/automation-model-overview.md)  
 Определяет модель автоматизации как связанные группы объектов, которые управляют важнейшими областями среде. Этот набор объектов, приведенное в схему модели автоматизации.  
  
 [Предоставление автоматизации для пакетов VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Рассматриваются два основных способа обеспечения автоматизации для VSPackage.  
  
 [Предоставление доступа к объектам проекта](../../extensibility/internals/exposing-project-objects.md)  
 Содержит пошаговые инструкции по созданию объекты, зависящие от пакета VSPackage.  
  
 [Моделирование проекта](../../extensibility/internals/project-modeling.md)  
 Объекты для стандартного проекта, где требуется создать автоматизацию для нового типа проекта объясняется и демонстрируется путь, который следует за автоматизации проектов. Здесь также приведены списки объявления и реализации для классов.  
  
 [Предоставление событий](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Содержит пошаговые инструкции по созданию события модели автоматизации.  
  
 [Поддержка автоматизации страниц параметров](../../extensibility/internals/automation-support-for-options-pages.md)  
 Описывает, как вернуть объект автоматизации, для поддержки свойств пакета VSPackage пользовательских **параметры** диалоговое окно в **средство** меню, расширяя `DTE.Properties` объекта.  
  
 [Предоставление автоматизации для кода](../../extensibility/internals/providing-automation-for-code.md)  
 Объясняет, что создание модели автоматизации для кода не требуется. Однако ссылка предоставляется в этом разделе, который предоставляет исчерпывающие сведения в модели кода.  
  
 [Практическое руководство. Автоматизация для окон](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Объясняет, предоставляя автоматизации, рекомендуется всякий раз, когда требуется освободить объекты автоматизации на окно и среде не предоставить объект готовых автоматизации. Описание автоматизации для окон инструментов и окна документов.  
  
 [Использование модели автоматизации](../../extensibility/internals/using-the-automation-model.md)  
 Предоставляет два примера кода, которые показывают, как потребитель автоматизации получает начального проекта, объекты автоматизации.  
  
 [Автоматизация для объектов конфигурации и SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Сведения об автоматизации для параметров конфигурации и автоматизации для выбранных элементов.  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Содержит пример кода, который показывает, как VSPackage участвует в объектной модели автоматизации DTE. Список параметров, возвращаемых значений и выбранного примечания.  
  
## <a name="related-sections"></a>Связанные разделы