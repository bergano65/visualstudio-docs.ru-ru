---
title: "Расширения отладчика Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c5b5943dc8087a22e1bdfb94ae6d0d10335c174a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-debugger-extensibility"></a>Расширения отладчика Visual Studio
Visual Studio включает отладчик полностью интерактивный исходного кода, предоставляет мощные и простые в использовании средства для отслеживания ошибок в программах. Отладчик имеет полную поддержку Visual Basic, C#, C/C++ и JavaScript. Однако в [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], в котором доступны из [центра загрузки Майкрософт](http://go.microsoft.com/fwlink/?LinkId=214453), других языках программирования, которые могут поддерживаться в отладчике с широкими возможностями, же.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отладчик находится общий внешний интерфейс (пользовательский интерфейс) для отладки компонентов, которые в свою очередь, относящиеся к языку, для которого выполняется отладка. Новые языки, необходимые для поддержки по [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладчик заключается в создании необходимых компонентов серверной части, такие как отладчик (DE). Именно так [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] поставляется в.  
  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Включает полный перечень ко всем [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] элементы, необходимые для создания нового DE. Кроме того существует, образцы и учебники, которые помогут приступить к работе.  
  
 Пример конца в конец языка системы проекта с поддержка отладки. в разделе [пример IronPython](http://msdn.microsoft.com/en-us/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 В следующих разделах описаны способы расширения отладчика с помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="in-this-section"></a>В этом разделе  
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Описывает, что [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки предложений и как установить пакет SDK.  
  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Документирует пользовательские DE процесс, Подготовка программы DE для отсоединения DE.  
  
 [Написание выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Объясняет, должен ли запись вычислитель выражений.  
  
 [Выбор стратегии реализации модуля отладки](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Описывает, как реализовать вашей DE.  
  
 [Ссылки](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Документы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API отладки.  
  
 [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Содержит ссылки на общие оценки образец выражения языка среды выполнения и образец ядра отладки.
