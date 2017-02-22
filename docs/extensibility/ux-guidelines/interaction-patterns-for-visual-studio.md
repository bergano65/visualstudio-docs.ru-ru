---
title: "Шаблоны взаимодействия для Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# Шаблоны взаимодействия для Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Обзор  
 Шаблон разработки, как правило, является основой конструктора, который может применяться в конкретных ситуациях для устранения проблем с похожими наборами ограничения. Конструкторы компонентов и системы использовать эти шаблоны проектирования как отправные точки, которые затем могут быть адаптированы для их конкретной ситуации.  
  
 Visual Studio имеется библиотека общих шаблонов взаимодействия, которые необходимо учитывать при создании новых функций. Два основных контекстов для наших шаблоны проектирования: клиента Visual Studio \(devenv\) и Visual Studio Online. Для некоторых проблем проектирования существует универсальной шаблон, который хорошо работает в любой ситуации. Во многих случаях однако решение может отличаться для пользовательского интерфейса, который представлен в браузере и, размещенную на клиентское приложение.  
  
### Типы шаблон Visual Studio клиента  
  
|Тип расписания|Описание|Примеры|  
|--------------------|--------------|-------------|  
|**Шаблоны уровня приложения**|Высокоуровневые шаблоны, общие для приложения, определение или отображение контекст приложения и содержащий составного и шаблонах элементов управления внутри них|-   Окна инструментов<br />-   Окна документов|  
|**Составные шаблоны**|Общие шаблоны, которые могут распространяться на шаблоны приложений или распознанный шаблон состоит из нескольких элементов управления в различных конфигурациях|-   Переключение представлений<br />-   Список построителей<br />-   Отображение данных<br />-   Уведомления<br />-   Проверка<br />-   Выбор модели|  
|**Шаблоны элементов управления**|Подробные сведения об элементах управления как низкоуровневые должны вести себя|-   Представление в виде дерева<br />-   Редактирование в элементе управления сетки|  
  
## Шаблоны приложений  
 На высоком уровне интерфейса Visual Studio включает в себя несколько windows, диалоговых окон, команд и панелей инструментов в одной интегрированной среды разработки. Иерархия Visual Studio определяет контекст и диски меню. Точек интеграции в пользовательском интерфейсе интегрированной среды разработки, окна документа, окна инструментов, проекты, структура команды, текстовый редактор, панели элементов, окно «Свойства» и средства \> Параметры.  
  
 Существует основное использование шаблонов для каждой из точек интеграции в пользовательском интерфейсе интегрированной среды разработки.  
  
-   [Меню и команд для Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Шаблоны приложений для Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Окно взаимодействия](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Окна инструментов](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Условные обозначения редактора](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [Диалоговые окна](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [Проекты](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## Общие шаблоны элементов управления  
 Шаблоны элементов управления являются главным образом о том, как отдельные элементы управления должны выполняться. Это единственная область, в которой согласованности является наиболее важным.  
  
 Наиболее распространенных элементов управления в Visual Studio должен следовать правилам рабочего стола Windows. Наши правила включаются только области, в которых нам нужно дополнить общие соглашения с Visual Studio конкретного взаимодействия или местах, в которых мы заменяют рекомендации полностью Чтобы настроить Visual Studio в соответствии с потребностями наших опытных пользователей.  
  
-   [Общие шаблоны элементов управления для Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Общие элементы управления](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Текстовые элементы управления](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [Кнопки и гиперссылки](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## Составные шаблоны  
 Существует ряд способов, которые пользователи ожидают, что для выполнения задач. По возможности функции должны быть рассчитаны на использовать эти закономерности для взаимодействия и визуальной разработки.  
  
 Хотя существует много составных шаблонов в среде Visual Studio, некоторые из наиболее важных отношении согласованности являются:  
  
-   [Составные шаблоны для Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [На объект пользовательского интерфейса и просмотр](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Выбор модели](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Сохранение состояния и сохранение параметров](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Сенсорный ввод](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)