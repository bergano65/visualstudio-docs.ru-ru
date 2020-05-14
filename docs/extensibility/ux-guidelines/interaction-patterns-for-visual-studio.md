---
title: Шаблоны взаимодействия для визуальной студии Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac917aeb2530570b755e7f1e6fc6de00714a54b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698374"
---
# <a name="interaction-patterns-for-visual-studio"></a>Шаблоны взаимодействия для Visual Studio
## <a name="overview"></a>Обзор
 Шаблон проектирования, как правило, является ядром конструкции, которая может быть применена в конкретных ситуациях для решения проблем с аналогичными наборами ограничений. Дизайнеры функций и систем используют эти шаблоны проектирования в качестве отправных точек, которые затем могут быть адаптированы к их конкретной ситуации.

 Visual Studio имеет библиотеку общих шаблонов взаимодействия, которые следует учитывать при создании новых функций. Есть два основных контекста для нашего дизайна моделей: Visual Studio Client (devenv) и Visual Studio Online. Для некоторых проблем проектирования существует вездесущий шаблон, который хорошо работает во всех ситуациях. Во многих случаях, однако, решение может быть различным для uI, который представлен в браузере и который размещается в клиентском приложении.

### <a name="visual-studio-client-pattern-types"></a>Типы шаблонов Visual Studio Client

|Тип шаблона|Описание|Примеры|
|------------------|-----------------|--------------|
|**Шаблоны уровня приложений**|Высокоуровневые шаблоны, общие для приложения, определяющие или отображающие контекст приложения, содержащие композитные и контрольные шаблоны внутри них|- Окна инструментов<br />- Окна документов|
|**Композитные узоры**|Общие шаблоны, которые могут охватывать шаблоны приложений, или признанный шаблон, состоящий из нескольких элементов управления в отдельной конфигурации|- Посмотреть переключение<br />- Список строителей<br />- Отображение данных<br />- Уведомления<br />- Проверка<br />- Модели выбора|
|**Шаблоны управления**|Специфика того, как будут вести себя низкоуровневые элементы управления|- Виды деревьев<br />- Редактирование в сетке управления|

## <a name="application-patterns"></a>Шаблоны приложений
 На высоком уровне интерфейс Visual Studio состоит из нескольких окон, диалогов, команд и панели инструментов в рамках одного IDE. Иерархия Visual Studio определяет контекст и приводит меню. Ключевыми точками интеграции в пользовательском интерфейсе IDE являются окна документов, окна инструментов, проекты, структура команды, текстовый редактор, набор инструментов, окно свойств и > опций.

 Существуют основные шаблоны использования для каждой из ключевых точек интеграции в пользовательском интерфейсе IDE:

- [Меню и команды для Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Шаблоны приложений для Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Взаимодействия окон](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Окна инструментов](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Конвенции редактора документов](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Диалоговые окна](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Проекты](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Общие шаблоны управления
 Шаблоны управления в основном о том, как индивидуальные элементы управления, как ожидается, будет вести себя. Это одна из областей, в которой согласованность является наиболее важным.

 Наиболее распространенные элементы управления в Visual Studio должны следовать рекомендациям Windows для настольных компьютеров. Наши руководящие принципы включают только области, в которых мы должны увеличить общие конвенции с Visual Studio конкретных взаимодействий, или места, в которых мы заменяем руководящие принципы полностью для того, чтобы адаптировать Visual Studio для удовлетворения потребностей наших сложных пользователей.

- [Шаблоны распространенных элементов управления для Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Общие элементы управления](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Текстовые элементы управления](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Кнопки и гиперссылки](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Композитные узоры
 Существует несколько способов выполнения задач пользователями. Там, где это возможно, функции должны быть разработаны для использования этих шаблонов как для взаимодействия и визуального дизайна.

 Хотя есть много составных моделей в Visual Studio, некоторые из наиболее важных в отношении согласованности являются:

- [Составные шаблоны для Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [На объекте uI и заглядывая](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Модели выбора](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Настойчивые и сохраняющие настройки](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Сенсорный ввод](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
