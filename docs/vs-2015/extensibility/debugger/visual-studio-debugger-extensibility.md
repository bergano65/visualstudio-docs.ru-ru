---
title: Расширяемость отладчика Visual Studio | Документация Майкрософт
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
ms.openlocfilehash: 0b8d37954bf238b2ed1323bf021fded94ec0c584
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "73983657"
---
# <a name="visual-studio-debugger-extensibility"></a>Расширяемость отладчика Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio включает в себя полностью интерактивный отладчик исходного кода, предоставляющий мощный и простой в использовании инструмент для отслеживания ошибок в программе. Отладчик имеет полную поддержку Visual Basic, C#, C/C++ и JavaScript. Однако в [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , который доступен в [центре загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=21835), другие языки программирования могут поддерживаться в отладчике с теми же широкими возможностями.  
  
 Отладчик является общим интерфейсным интерфейсом [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (таким, как пользовательского интерфейса) для отладочных компонентов, которые, в свою очередь, специфичны для отлаживаемого языка. Для новых языков, необходимых для поддержки [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладчика, необходимо создать необходимые серверные компоненты, такие как модуль отладки (de). Именно здесь входит в [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Содержит полную ссылку на все элементы, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] необходимые для создания нового de. Кроме того, есть примеры и учебники, которые помогут вам приступить к работе.  
  
 Полный пример системы проектного языка с поддержкой отладки см. в [образце IronPython](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 В следующих разделах описывается расширение отладчика с помощью [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
## <a name="in-this-section"></a>в этом разделе  
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Описание [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] предложений по отладке и установки пакета SDK.  
  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Документирует пользовательский процесс DE, от подготовки программы к отсоединению de.  
  
 [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Объясняет, нужно ли писать средство оценки выражений.  
  
 [Выбор стратегии реализации модуля отладки](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Описывает, как реализовать метод DE.  
  
 [Ссылки](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Документирует [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] API отладки.  
  
 [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Содержит ссылки на пример средства оценки выражений среды CLR и пример модуля отладки.
