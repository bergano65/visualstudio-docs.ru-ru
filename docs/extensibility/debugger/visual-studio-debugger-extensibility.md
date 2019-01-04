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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 55a6c0098779b96592335c4f74309338e8089e97
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822736"
---
# <a name="visual-studio-debugger-extensibility"></a>Расширяемость отладчика Visual Studio
Visual Studio включает отладчик полностью интерактивные исходного кода, предоставляет мощный и простой в использовании средство для ошибок в программе. Отладчик имеет полную поддержку Visual Basic, C#, C/C++ и JavaScript. Тем не менее, с помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], то есть доступны из [центра загрузки Майкрософт](http://go.microsoft.com/fwlink/?LinkId=214453), другие языки программирования, которые могут поддерживаться в отладчике с тем же широкими возможностями.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отладчика — общий интерфейс (то есть пользовательский интерфейс) отладки компонентов, которые в свою очередь, относящиеся к языку, для которого выполняется отладка. Для новых языков, необходимые для поддержки по [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладчика — создать необходимые компоненты серверной части, например модуля отладки (DE). Именно для этой точки [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] пригодиться.  
  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Включает в себя полный Справочник ко всем [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] элементы, необходимые для создания нового DE. Кроме того существуют, примеры и учебники, которые помогут приступить к работе.  
  
 Полный пример языка системы проекта с отладкой поддержки, см. в разделе [пример IronPython](https://www.microsoft.com/download/details.aspx?id=55984).  
  
 В следующих разделах рассматривается расширение отладчика с помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Описывается, что [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки предложения и установка пакета SDK.  
  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Документирует пользовательские DE процесс, от подготовки программы для DE для отсоединения DE.  
  
 [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Объясняется ли необходимо написать вычислитель выражений.  
  
 [Выбор стратегии реализации модуля отладки](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Обсуждаются способы применения вашей DE.  
  
 [Ссылки](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Документы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API отладки.  
  
 [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Содержит ссылки на общий вычислителя пример выражения языка среды выполнения и образец ядра отладки.
