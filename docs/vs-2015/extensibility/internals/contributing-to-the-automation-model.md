---
title: Дополнение к модели автоматизации | Документация Майкрософт
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196996"
---
# <a name="contributing-to-the-automation-model"></a>Contributing to the Automation Model
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio предоставляет набор интерфейсов автоматизации для настройки среды. Модель автоматизации — объектная модель, который позволяет конечным пользователям для создания надстроек Visual Studio и расширения.  
  
 Кроме того это наиболее подходящего для вас, как разработчик VSPackage участвовать в модели автоматизации; Таким образом разрешить конечным пользователям вашего VSPackage для создания надстроек и предоставляют согласованный пользовательский интерфейс модели при использовании пакета VSPackage в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Согласованность работы конечного пользователя, необходимо выполнить набор рекомендаций по разработке VSPackage, чтобы модель автоматизации для VSPackage следует за идеи в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>В этом разделе  
 [Общие сведения о модели автоматизации](../../extensibility/internals/automation-model-overview.md)  
 Определяет модель автоматизации как связанные группы объектов, которые управляют важнейшими областями среде. Этот набор объектов, изображенного на схеме модели автоматизации.  
  
 [Предоставление автоматизации для пакетов VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Рассматриваются два основных способа для предоставления службы автоматизации для VSPackage.  
  
 [Предоставление доступа к объектам проекта](../../extensibility/internals/exposing-project-objects.md)  
 Предоставляет пошаговые инструкции по созданию объектов определенного VSPackage.  
  
 [Моделирование проекта](../../extensibility/internals/project-modeling.md)  
 Для стандартного проекта объекты, необходимые для создания службы автоматизации для нового типа проекта объясняется и демонстрируется путь, который следует за автоматизации проектов. Здесь также приведены Листинги объявления и реализации для классов.  
  
 [Предоставление доступа к событиям](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Содержит пошаговые инструкции по созданию события для модели автоматизации.  
  
 [Поддержка автоматизации страниц параметров](../../extensibility/internals/automation-support-for-options-pages.md)  
 Описывается, как вернуть объект автоматизации для поддержки свойства VSPackage пользовательских **параметры** диалоговое окно на **средство** меню, расширив `DTE.Properties` объекта.  
  
 [Предоставление автоматизации для кода](../../extensibility/internals/providing-automation-for-code.md)  
 Объясняет, что создание модели автоматизации для кода не требуется. Тем не менее в этом разделе, который предоставляет полезную информацию в модели кода предоставляется ссылка.  
  
 [Практическое руководство. Автоматизация для окон](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Объясняет, что предоставление автоматизации является хорошей идеей, всякий раз, когда вы хотите сделать объекты автоматизации доступными в окне и среде уже не предоставить объект готовые службы автоматизации. Описание автоматизации для окон инструментов и окон документов.  
  
 [Использование модели автоматизации](../../extensibility/internals/using-the-automation-model.md)  
 Предоставляет два примера кода, в которых показано, как потребитель автоматизации получает начального проекта, объекты автоматизации.  
  
 [Автоматизация для объектов конфигурации и SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Сведения о службе автоматизации для параметров конфигурации и автоматизации для выбранных элементов.  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Представлен пример кода, показывающий, как VSPackage участвует в объектной модели автоматизации DTE. Перечисляются параметры, возвращаемые значения и выбранные "Примечания".  
  
## <a name="related-sections"></a>Связанные разделы
