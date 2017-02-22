---
title: "Расширение возможностей отладчика Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [Visual Studio], пакет SDK для отладки"
  - "Пакет SDK для отладки"
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 32
caps.handback.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
---
# Расширение возможностей отладчика Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio включает отладчик полностью интерактивным исходного кода, предоставляя мощные и простые в использовании средства для отслеживания ошибок в программах. Отладчик имеет полную поддержку Visual Basic, C\#, C\/C\+\+ и JavaScript. Тем не менее, с [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], который доступен из [центра загрузки Майкрософт](http://go.microsoft.com/fwlink/?LinkId=214453),, поддерживается в отладчике с широкими возможностями, же других языков программирования.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Компоненты отладки, которые в свою очередь, относящиеся к языку отлаживаемой отладчика является общий интерфейс \(пользовательский интерфейс\). Новые языки, необходимые для поддержки по [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладчика — создать необходимые компоненты серверной части, такие как отладчик \(DE\). Именно [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] могут пригодиться.  
  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Включает полные ссылки на все [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] элементы, необходимые для создания нового DE. Кроме того существуют примеры и учебники, которые помогут приступить к работе.  
  
 Пример end\-to\-end языка системы проекта с поддержки отладки в разделе [IronPython sample](http://msdn.microsoft.com/ru-ru/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 В следующих разделах описаны способы расширения отладчика с помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
## В этом подразделе  
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Описание [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки предложения и установка пакета SDK.  
  
 [Создание пользовательские отладки ядра](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Документирует пользовательский процесс DE из Подготовка программы DE для отсоединения DE.  
  
 [Написание вычислитель выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Объясняет ли необходимо написать средство оценки выражений.  
  
 [Выбор стратегии реализации ядра отладки](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Описывает, как реализовать вашей DE.  
  
 [Ссылки](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Документы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API отладки.  
  
 [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Содержит ссылки на общие оценки образец выражения языка среды выполнения и образец ядра отладки.