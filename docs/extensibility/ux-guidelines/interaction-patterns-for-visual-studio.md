---
title: Шаблоны взаимодействия для Visual Studio | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3a0e4d0a6623b142519f78603218df4e604e805
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723374"
---
# <a name="interaction-patterns-for-visual-studio"></a>Шаблоны взаимодействия для Visual Studio
## <a name="overview"></a>Обзор
 Шаблон разработки, как правило, является основой разработки, которые могут применяться в конкретных ситуациях для решения проблем с похожими наборами ограничения. Конструкторы компонентов и системы использовать эти шаблоны проектирования в качестве отправных точек, которые затем можно адаптировать для их конкретной ситуации.

 Visual Studio содержит библиотеку стандартных шаблонов взаимодействия, которые необходимо учитывать при создании новых функций. Существует два основных контекста для наших шаблонов проектирования. Клиент Visual Studio (devenv) и Visual Studio Online. Для некоторых проблем проектирования имеется повсеместно шаблон, который хорошо работает в любой ситуации. Во многих случаях однако решение может отличаться для пользовательского интерфейса, который представляется в браузере и, которая размещается на клиентское приложение.

### <a name="visual-studio-client-pattern-types"></a>Типах шаблонов Visual Studio клиента

|Тип расписания|Описание|Примеры|
|------------------|-----------------|--------------|
|**Шаблоны уровня приложения**|Высокоуровневых шаблона, общие для приложения, определение или отображение контекст приложения и содержащий составного и шаблоны элементов управления в них|-Windows средство<br />-Windows документа|
|**Составные шаблоны**|Общие шаблоны, которые могут охватывать во всех приложениях или распознанным шаблон состоит из нескольких элементов управления в различных конфигурации|-Переключение представлений<br />-Построители list<br />— Отображение данных<br />-Уведомления<br />— Проверка<br />-Выбор модели|
|**Шаблоны элементов управления**|Сведения об элементах управления как низкоуровневые ожидаемом поведении|-В древовидном представлении<br />-Редактирования в элементе управления сетки|

## <a name="application-patterns"></a>Шаблоны приложений
 На высоком уровне интерфейсе Visual Studio состоит из нескольких windows, диалоговых окон, команд и панелей инструментов в одну интегрированную среду разработки. Иерархии Visual Studio определяет контекст, а также диски меню. Ключевые точки интеграции в пользовательском интерфейсе интегрированной среды разработки, окна документов, окон инструментов, проектов, структура команд, текстовый редактор, панели элементов, окно "Свойства" и инструменты > Параметры.

 Существуют шаблоны основные сценарии использования для каждой из точек интеграции в пользовательском интерфейсе интегрированной среды разработки:

-   [Меню и команды для Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

-   [Шаблоны приложений для Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

    -   [Окно взаимодействия](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

    -   [Окна инструментов](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

    -   [Условные обозначения редактора](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

    -   [Диалоговые окна](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

    -   [Проекты](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Шаблоны стандартных элементов управления
 Шаблоны элементов управления являются главным образом, сведения об отдельных элементах управления ожидаемом поведении. Это единственная область, в которой наиболее важно согласованности.

 Наиболее распространенных элементов управления в Visual Studio следует придерживаться рекомендаций, рабочего стола Windows. Наши правила включают только области, в которых нам нужно дополнить общие соглашения с Visual Studio конкретных взаимодействия или местах, в которых мы заменяют рекомендации полностью чтобы адаптировать Visual Studio в соответствии с потребностями наших опытных пользователей.

-   [Шаблоны распространенных элементов управления для Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

    -   [Общие элементы управления](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

    -   [Текстовые элементы управления](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

    -   [Кнопки и гиперссылки](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Составные шаблоны
 Существует ряд способов, пользователи ожидают, что для выполнения задач. По возможности функции должно уметь использовать эти закономерности для взаимодействия и визуального проектирования.

 Хотя существует много составные шаблоны в Visual Studio, некоторые из наиболее важных отношении согласованности являются:

-   [Составные шаблоны для Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

    -   [На объект пользовательского интерфейса и просмотр](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

    -   [Выбор модели](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

    -   [Сохраняемости и сохранения параметров](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

    -   [Реакция на сенсорный ввод](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)