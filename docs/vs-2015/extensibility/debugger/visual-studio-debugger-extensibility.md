---
title: Расширение возможностей отладчика Visual Studio | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 528716c4ea354ab63dc7fcab2b3f90fe2860b655
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989960"
---
# <a name="visual-studio-debugger-extensibility"></a>Расширяемость отладчика Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio включает отладчик полностью интерактивные исходного кода, предоставляет мощный и простой в использовании средство для ошибок в программе. Отладчик имеет полную поддержку Visual Basic, C#, C/C++ и JavaScript. Тем не менее, с помощью [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], то есть доступны из [центра загрузки Майкрософт](http://go.microsoft.com/fwlink/?LinkId=214453),, другие языки программирования, которые могут поддерживаться в отладчике с тем же широкими возможностями.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Отладчика — общий интерфейс (то есть пользовательский интерфейс) отладки компонентов, которые в свою очередь, относящиеся к языку, для которого выполняется отладка. Для новых языков, необходимые для поддержки по [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладчика — создать необходимые компоненты серверной части, например модуля отладки (DE). Именно здесь [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] пригодиться.  
  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Включает в себя полный Справочник ко всем [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] элементы, необходимые для создания нового DE. Кроме того существуют, примеры и учебники, которые помогут приступить к работе.  
  
 Пример end-to-end языка системы проекта с отладкой поддержки, см. в разделе [пример IronPython](http://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 В следующих разделах рассматривается расширение отладчика с помощью [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
## <a name="in-this-section"></a>В этом разделе  
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Описывается, что [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладки предложения и установка пакета SDK.  
  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Документирует пользовательские DE процесс, от подготовки программы для DE для отсоединения DE.  
  
 [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Объясняется ли необходимо написать вычислитель выражений.  
  
 [Выбор стратегии реализации модуля отладки](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Обсуждаются способы применения вашей DE.  
  
 [Ссылки](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Документы [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] API отладки.  
  
 [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Содержит ссылки на общий вычислителя пример выражения языка среды выполнения и образец ядра отладки.
