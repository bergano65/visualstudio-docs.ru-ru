---
title: Вклад в модель автоматизации | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c84ea078f9b7c1268b765111cc400f6e51b783f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196996"
---
# <a name="contributing-to-the-automation-model"></a>Contributing to the Automation Model
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio предоставляет набор интерфейсов автоматизации для настройки среды. Модель автоматизации — это объектная модель, позволяющая конечным пользователям создавать надстройки и расширения Visual Studio.  
  
 Кроме того, в качестве разработчика VSPackage подходит для участия в модели автоматизации. Это позволит пользователям пакета VSPackage создавать надстройки и, как правило, обеспечить единообразную модель пользователя при использовании VSPackage в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Чтобы обеспечить единообразное взаимодействие с конечным пользователем, вы можете следовать набору рекомендаций по разработке пакета VSPackage, чтобы модель автоматизации пакета VSPackage соответствовала идеям в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="in-this-section"></a>в этом разделе  
 [Общие сведения о модели автоматизации](../../extensibility/internals/automation-model-overview.md)  
 Определяет модель автоматизации как связанные группы объектов, которые управляют основными аспектами общей среды. Этот набор объектов изображен на схеме модели автоматизации.  
  
 [Предоставление автоматизации для пакетов VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Обсуждаются два основных способа предоставления автоматизации для VSPackage.  
  
 [Предоставление доступа к объектам проекта](../../extensibility/internals/exposing-project-objects.md)  
 Содержит пошаговые инструкции по созданию объектов, зависящих от VSPackage.  
  
 [Моделирование проекта](../../extensibility/internals/project-modeling.md)  
 Описание стандартных объектов проекта, необходимых для создания автоматизации для нового типа проекта, и показан путь, который следует за автоматизацией проекта. В этом разделе также приводятся списки объявлений и реализации классов.  
  
 [Предоставление доступа к событиям](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Содержит пошаговые инструкции по созданию событий для модели автоматизации.  
  
 [Поддержка автоматизации страниц параметров](../../extensibility/internals/automation-support-for-options-pages.md)  
 Описывает, как вернуть объект автоматизации для поддержки свойств диалогового окна пользовательских **параметров** VSPackage в меню **инструментов** , расширив `DTE.Properties` объект.  
  
 [Предоставление автоматизации для кода](../../extensibility/internals/providing-automation-for-code.md)  
 Объясняется, что создание модели автоматизации для кода не является обязательным. Однако в этом разделе приведена ссылка, которая предоставляет сведения о моделях кода.  
  
 [Практическое руководство. Автоматизация для окон](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Объясняется, что предоставление автоматизации является хорошей идеей при необходимости сделать объекты автоматизации доступными в окне, а среда еще не предоставляет готовый объект автоматизации. Описывает автоматизацию для окон инструментов и окон документов.  
  
 [Использование модели автоматизации](../../extensibility/internals/using-the-automation-model.md)  
 Содержит два примера кода, демонстрирующих, как потребитель автоматизации получает исходные объекты автоматизации проекта.  
  
 [Автоматизация для объектов конфигурации и SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Предоставляет сведения об автоматизации для параметров конфигурации и автоматизации для выбранных элементов.  
  
## <a name="reference"></a>Справочник  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Содержит пример кода, показывающий, как VSPackage участвует в объектной модели автоматизации DTE. Перечисляет параметры, возвращаемые значения и выбранные примечания.  
  
## <a name="related-sections"></a>См. также
