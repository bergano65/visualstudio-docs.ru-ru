---
title: Расширяемость отладчика Visual Studio | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f8a1c2148f25a1e97cfd1369770e056d1cb907d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568970"
---
# <a name="visual-studio-debugger-extensibility"></a>Расширяемость отладчика Visual Studio
Visual Studio включает в себя полностью интерактивный отладчик исходного кода, предоставляющий мощный и простой в использовании инструмент для отслеживания ошибок в программе. Отладчик полностью поддерживает Visual Basic, C#, C/C++и JavaScript. Однако с [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], который доступен в [центре загрузки Майкрософт](http://go.microsoft.com/fwlink/?LinkId=214453), другие языки программирования могут поддерживаться в отладчике с теми же широкими возможностями.

 Отладчик [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] — это общий интерфейс (т. е. пользовательского интерфейса) для отладочных компонентов, которые, в свою очередь, специфичны для отлаживаемого языка. Для новых языков, необходимых для поддержки с помощью отладчика [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], необходимо создать необходимые серверные компоненты, такие как модуль отладки (DE). На этом этапе [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] поступает в.

 @No__t_0 содержит полную ссылку на все элементы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], необходимые для создания нового DE. Кроме того, есть примеры и учебники, которые помогут вам приступить к работе.

 Полный пример системы проектного языка с поддержкой отладки см. в [образце IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 В следующих разделах описано, как расширить отладчик с помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>В данном разделе
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Описывает, какие предложения отладки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и как установить пакет SDK.

 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md) Документирует пользовательский процесс DE, от подготовки программы к отсоединению de.

 [Написание вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Объясняет, нужно ли писать средство оценки выражений.

 [Выбор стратегии реализации модуля отладки](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Описывает, как реализовать метод DE.

 [Справочные материалы](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Документирует [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API отладки.

 [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md) Содержит ссылки на пример средства оценки выражений среды CLR и пример модуля отладки.
