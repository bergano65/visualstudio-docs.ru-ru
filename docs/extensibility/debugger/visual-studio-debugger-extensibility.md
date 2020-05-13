---
title: Визуальная студия Exbugger Расширяемость (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff4222b555fab73914776725fc79581f29fa5e53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712502"
---
# <a name="visual-studio-debugger-extensibility"></a>Эффектная студия отладчика расширяемые
Visual Studio включает в себя полностью интерактивный отладчик исходного кода, обеспечивая мощный и простой в использовании инструмент для отслеживания ошибок в вашей программе. Отладчик имеет полную поддержку visual Basic, C,, C/C и JavaScript. Тем не [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]менее, с , который доступен из [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=21835), другие языки программирования могут быть поддержаны в отладчик с теми же богатыми функциями.

 Отладчик [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] является общим передним концом (т.е. пользовательским интерфейсом) для компонентов отладки, которые, в свою очередь, специфичны для отладительной связи. Для новых языков все, что необходимо [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для поддержки отладчиком, это создание необходимых компонентов бэк-энда, таких как отладка двигателя (DE). Этот момент, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] где приходит дюйма

 Включает [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] в себя полную ссылку на все [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] элементы, необходимые для создания нового DE. Кроме того, Есть образцы и учебники, которые помогут вам начать.

 Полный образец языковой проектной системы с [IronPython sample](https://www.microsoft.com/download/details.aspx?id=55984)поддержкой отладки см.

 В следующих разделах описывается, как [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]расширить отладчик с помощью .

## <a name="in-this-section"></a>В этом разделе
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Описывает, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] что предлагает Debugging и как установить SDK.

 [Создание пользовательского движка отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md) Документы пользовательский процесс DE, от подготовки программы для DE для отсоединения DE.

 [Написать оценщика экспрессии CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Объясняет, следует ли написать оценщика выражения.

 [Выберите стратегию внедрения движка отладки](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Обсуждает, как реализовать de.

 [Справка](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Документы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API debugging.

 [Образцы](../../extensibility/debugger/visual-studio-debugging-samples.md) Содержит ссылки на образец оценителя выражения времени выполнения общего языка и образец двигателя отладки.
