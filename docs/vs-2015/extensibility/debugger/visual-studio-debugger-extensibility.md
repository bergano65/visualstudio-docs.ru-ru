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
ms.sourcegitcommit: 3a19319e2599bd193fb2ca32020ca53942974bfd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983657"
---
# <a name="visual-studio-debugger-extensibility"></a>Расширяемость отладчика Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio включает в себя полностью интерактивный отладчик исходного кода, предоставляющий мощный и простой в использовании инструмент для отслеживания ошибок в программе. Отладчик имеет полную поддержку Visual Basic, C#, C/C++и JavaScript. Однако с [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], который доступен в [центре загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=21835), другие языки программирования могут поддерживаться в отладчике с теми же широкими возможностями.  
  
 Отладчик [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] — это общий интерфейс (т. е. пользовательского интерфейса) для отладочных компонентов, которые, в свою очередь, специфичны для отлаживаемого языка. Для новых языков, необходимых для поддержки с помощью отладчика [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], необходимо создать необходимые серверные компоненты, такие как модуль отладки (DE). Здесь [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] входит в.  
  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] содержит полную ссылку на все элементы [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], необходимые для создания нового DE. Кроме того, есть примеры и учебники, которые помогут вам приступить к работе.  
  
 Полный пример системы проектного языка с поддержкой отладки см. в [образце IronPython](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 В следующих разделах описано, как расширить отладчик с помощью [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
## <a name="in-this-section"></a>Содержание  
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Описывает, какие предложения отладки [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и как установить пакет SDK.  
  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Документирует пользовательский процесс DE, от подготовки программы к отсоединению de.  
  
 [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Объясняет, нужно ли писать средство оценки выражений.  
  
 [Выбор стратегии реализации модуля отладки](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Описывает, как реализовать метод DE.  
  
 [Ссылка](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Документирует [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] API отладки.  
  
 [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Содержит ссылки на пример средства оценки выражений среды CLR и пример модуля отладки.
