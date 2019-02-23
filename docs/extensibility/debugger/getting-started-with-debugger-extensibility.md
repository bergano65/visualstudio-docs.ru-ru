---
title: Приступая к работе с расширением отладчика | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f3fe14cff05f37ef7ee6f10026fd727696a223f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696055"
---
# <a name="get-started-with-debugger-extensibility"></a>Начало работы с расширением отладчика
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Предоставляет информацию, необходимую для создания и настройки компонентов отладчик, используемый для отладки программы изнутри [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладку добавленные усовершенствования, производным от обширной удобство использования, тестирование на предыдущем [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладчики. Можно использовать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки для пошагового выполнения приложения Многоязычная версия, или можно реализовать на лету редактирования переменных при отладке приложения и решения для нескольких языков.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отладка — выполненных вне процесса с отлаживаемой программы, поэтому меньше вмешивается в пространстве процесса приложения. Следовательно проще создавать компоненты, которые взаимодействуют с помощью отладчика не затрагивая отладки программы.

 Чтобы максимально эффективно использовать [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], необходимо ознакомиться со следующими элементами:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированной среды разработки (IDE)

- Языка программирования C++

- ATL COM

## <a name="in-this-section"></a>Содержание раздела
 [Схема для расширения отладчика](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) описание процесса реализации отладки в ваш продукт, в зависимости от вашего компилятора и его выходные данные.

 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md) Обзор [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладка компонентов, которые включают модуль отладки (DE), средство оценки выражений (EE) и символ обработчик (SH).

 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md) описывает основные архитектурные понятия отладки.

 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md) объясняется, как модуль отладки (DE) работает одновременно в контекстах оценки кода, документацию и выражение. Описание для каждого из трех контекстов, расположение, положения или оценки, относящиеся к его.

 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md) содержит ссылки на различные задачи отладки, такие как запуск программы и оценки выражений.