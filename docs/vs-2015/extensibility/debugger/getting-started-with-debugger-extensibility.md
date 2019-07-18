---
title: Приступая к работе с расширением отладчика | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1c616c7cf8ed90ec3d76046892167b9b742a1b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152710"
---
# <a name="getting-started-with-debugger-extensibility"></a>Приступая к работе с расширением отладчика
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Предоставляет сведения, которые необходимы для создания и настройки компонентов отладчик, используемый для отладки программы изнутри [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] среды.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладку добавленные усовершенствования, производным от обширной удобство использования, тестирование на предыдущем [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладчики. Можно использовать [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладки для пошагового выполнения приложения Многоязычная версия, или можно реализовать на лету редактирования переменных при отладке приложения и решения для нескольких языков.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Отладка — выполненных вне процесса с отлаживаемой программы, поэтому меньше вмешивается в пространстве процесса приложения. Следовательно проще создавать компоненты, которые взаимодействуют с помощью отладчика не затрагивая отладки программы.  
  
 Чтобы максимально эффективно использовать [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], необходимо ознакомиться со следующими:  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Интегрированной среды разработки (IDE)  
  
- Языка программирования C++  
  
- ATL COM  
  
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
