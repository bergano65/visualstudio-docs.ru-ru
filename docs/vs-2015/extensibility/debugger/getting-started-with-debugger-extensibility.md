---
title: Приступая к работе с расширением отладчика | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f8f056ed8fff53eb166b37f2adba9daa17f12916
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568184"
---
# <a name="getting-started-with-debugger-extensibility"></a>Приступая к работе с расширением отладчика
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Приступая к работе с расширением отладчика](https://docs.microsoft.com/visualstudio/extensibility/debugger/getting-started-with-debugger-extensibility).  
  
[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Предоставляет сведения, которые необходимы для создания и настройки компонентов отладчик, используемый для отладки программы изнутри [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] среды.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладку добавленные усовершенствования, производным от обширной удобство использования, тестирование на предыдущем [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладчики. Можно использовать [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладки для пошагового выполнения приложения Многоязычная версия, или можно реализовать на лету редактирования переменных при отладке приложения и решения для нескольких языков.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Отладка — выполненных вне процесса с отлаживаемой программы, поэтому меньше вмешивается в пространстве процесса приложения. Следовательно проще создавать компоненты, которые взаимодействуют с помощью отладчика не затрагивая отладки программы.  
  
 Чтобы максимально эффективно использовать [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], необходимо ознакомиться со следующими:  
  
-   [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Интегрированной среды разработки (IDE)  
  
-   Языка программирования C++  
  
-   ATL COM  
  
## <a name="in-this-section"></a>В этом разделе  
 [Схема для расширения отладчика](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Описание процесса реализации отладки в ваш продукт, в зависимости от вашего компилятора и его выходные данные.  
  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)  
 Общие сведения о [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладка компонентов, которые включают модуль отладки (DE), средство оценки выражений (EE) и символ обработчик (SH).  
  
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные архитектурные понятия отладки.  
  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)  
 Объясняет, как модуль отладки (DE) действует одновременно в пределах кода, документацию и контекстов вычисления выражения. Описание для каждого из трех контекстов, расположение, положения или оценки, относящиеся к его.  
  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)  
 Содержит ссылки на различные задачи отладки, такие как запуск программы и оценки выражений.

