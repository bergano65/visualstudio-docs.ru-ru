---
title: Шаблоны взаимодействия для Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 094e16fea46e459dd64338ffa5daf3f7b98afb90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="interaction-patterns-for-visual-studio"></a>Шаблоны взаимодействия для Visual Studio
## <a name="overview"></a>Обзор  
 Шаблон проектирования в общем случае является основой для проектирования, которая может применяться в конкретных ситуациях для устранения проблем с похожими наборами ограничения. Конструкторы компонентов и системы используют эти шаблоны проектирования качестве начальных точек, которые затем могут быть настроены на их конкретной ситуации.  
  
 Visual Studio использует библиотеку общих шаблонов взаимодействия, которые следует учитывать при создании новых функций. Существует два основных контекстов для наших шаблонов разработки: клиента Visual Studio (devenv) и Visual Studio Online. Для некоторых проблем разработки есть единый шаблон, который хорошо работает в любой ситуации. Во многих случаях однако решение может отличаться для пользовательского интерфейса, которая содержится в веб-браузер и, который размещается на клиентское приложение.  
  
### <a name="visual-studio-client-pattern-types"></a>Типах шаблонов Visual Studio клиента  
  
|Тип расписания|Описание|Примеры|  
|------------------|-----------------|--------------|  
|**Шаблоны уровня приложения**|Высокоуровневые шаблоны, общие для приложения, определение или отображение контекст приложения и содержащий составную и шаблоны элементов управления в них|-Windows средство<br />-Windows документа|  
|**Составные шаблоны**|Общие шаблоны, которые могут охватывать шаблоны приложений или распознанный шаблон состоит из нескольких элементов управления в различных конфигурациях|-Переключение представлений<br />-Построители list<br />-Отображение данных<br />-Уведомления<br />-Проверка<br />-Выбор модели|  
|**Шаблоны элементов управления**|Подробные сведения об элементах управления как низкоуровневые должны вести себя|-Представления в виде дерева<br />-Изменения в элемент управления DataGrid|  
  
## <a name="application-patterns"></a>Шаблоны приложений  
 На высоком уровне в интерфейс Visual Studio включает в себя несколько окон, диалоговых окон, команд и панелей инструментов в одной интегрированной среде разработки. Иерархия Visual Studio определяет контекст, а диски меню. Точки интеграции в пользовательском интерфейсе интегрированной среды разработки, окна документов, окон инструментов, проекты, структуру команды, текстовый редактор, панели элементов, окно "Свойства" и средства > Параметры.  
  
 Существуют шаблоны простейшие варианты использования для каждой из точек интеграции в пользовательском интерфейсе интегрированной среды разработки:  
  
-   [Меню и команды для Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Шаблоны приложений для Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Окно взаимодействия](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Окна инструментов](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Условные обозначения редактора](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [Диалоговые окна](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [Проекты](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## <a name="common-control-patterns"></a>Общие шаблоны элементов управления  
 Шаблоны элементов управления являются главным образом, сведения об отдельных элементах управления должны вести себя. Это единственная область, в которой наиболее важно согласованности.  
  
 Наиболее распространенных элементов управления в Visual Studio следует придерживаться рекомендаций, рабочий стол Windows. Рекомендации включают только области, в которых нужно расширить общих соглашений с Visual Studio конкретного взаимодействия или местах, в которых мы заменяют рекомендации полностью Чтобы настроить Visual Studio для удовлетворения требований наших пользователям.  
  
-   [Шаблоны распространенных элементов управления для Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Общие элементы управления](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Текстовые элементы управления](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [Кнопки и гиперссылки](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## <a name="composite-patterns"></a>Составные шаблоны  
 Существует ряд способов, которые пользователи ожидают, что для выполнения задач. Везде, где это возможно, необходимо предусмотреть возможности использовать эти закономерности для взаимодействия и визуальной разработки.  
  
 Хотя существует много составные шаблоны в среде Visual Studio, некоторые из наиболее важных отношении согласованности являются:  
  
-   [Составные шаблоны для Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [На объект пользовательского интерфейса и просмотр](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Выбор модели](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Сохраняемости и сохранения параметров](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Сенсорный ввод](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)