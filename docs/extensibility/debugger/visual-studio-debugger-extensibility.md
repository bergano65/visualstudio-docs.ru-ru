---
title: Расширение возможностей отладчика Visual Studio | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df9d1bccb2147d8416555099f3493ceac8c21b4b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704804"
---
# <a name="visual-studio-debugger-extensibility"></a>Расширяемость отладчика Visual Studio
Visual Studio включает отладчик полностью интерактивные исходного кода, предоставляет мощный и простой в использовании средство для ошибок в программе. Отладчик имеет полную поддержку Visual Basic, C#, C/C++ и JavaScript. Тем не менее, с помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], то есть доступны из [центра загрузки Майкрософт](http://go.microsoft.com/fwlink/?LinkId=214453), другие языки программирования, которые могут поддерживаться в отладчике с тем же широкими возможностями.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отладчика — общий интерфейс (то есть пользовательский интерфейс) отладки компонентов, которые в свою очередь, относящиеся к языку, для которого выполняется отладка. Для новых языков, необходимые для поддержки по [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладчика — создать необходимые компоненты серверной части, например модуля отладки (DE). Именно для этой точки [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] пригодиться.

 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Включает в себя полный Справочник ко всем [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] элементы, необходимые для создания нового DE. Кроме того существуют, примеры и учебники, которые помогут приступить к работе.

 Полный пример языка системы проекта с отладкой поддержки, см. в разделе [пример IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 В следующих разделах рассматривается расширение отладчика с помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>Содержание раздела
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) описывается, что [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки предложения и установка пакета SDK.

 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md) Документирует пользовательский процесс DE, от подготовки программы для DE для отсоединения DE.

 [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) объясняется ли необходимо написать вычислитель выражений.

 [Выбор стратегии реализации модуля отладки](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) обсуждается реализация вашей DE.

 [Справочник по](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) документов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API отладки.

 [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md) содержит ссылки на общий вычислителя пример выражения языка среды выполнения и образец ядра отладки.
