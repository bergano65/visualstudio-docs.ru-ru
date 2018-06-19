---
title: Приступая к работе с расширения отладчика | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98d6e0200c1a68ae3819d3276ce8a04aaada2e78
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102698"
---
# <a name="getting-started-with-debugger-extensibility"></a>Приступая к работе с расширения отладчика
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Содержатся сведения, которые необходимы для создания и настройки компонентов отладчик позволяет отлаживать программы изнутри [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отладка добавил усовершенствования производными широко удобство использования тестированию на предыдущем [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладчики. Можно использовать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки для пошагового выполнения приложения говорящих на разных языках, или можно реализовать на лету редактирование переменных при отладке приложения и решения, говорящих на разных языках.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отладка — выполненных out-of-process с отлаживаемой программы, поэтому меньше вмешивается в пространство процесса приложения. Следовательно проще создавать компоненты, которые взаимодействуют с отладчиком не затрагивая отладки программы.  
  
 Лучше использовать [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], следует ознакомиться со следующими:  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированной среды разработки (IDE)  
  
-   Язык программирования C++  
  
-   ATL COM  
  
## <a name="in-this-section"></a>В этом разделе  
 [Схема для расширения отладчика](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Описание процесса реализации отладки в продукт, в зависимости от того, компилятор и результаты ее выполнения.  
  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)  
 Общие сведения о [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладка компонентов, которые включают модуль отладки (DE), средство оценки выражений (EE) и обработчик символ (SH).  
  
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные принципы отладки архитектуры.  
  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)  
 Объясняет, как модуль отладки (DE) одновременно работает в пределах кода, документацию и контекстов выражения вычисления. Описание для каждого из трех контекстов, расположения, положение или оценки, относящиеся к нему.  
  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)  
 Содержит ссылки на различные задачи отладки, например, запустив программу и оценки выражений.