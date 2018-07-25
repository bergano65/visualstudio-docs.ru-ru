---
title: Приступая к работе с расширением отладчика | Документация Майкрософт
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
ms.openlocfilehash: e1a812575d14ef6595d58cc3ecc5d9f94b8f5635
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231292"
---
# <a name="get-started-with-debugger-extensibility"></a>Начало работы с расширением отладчика
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Предоставляет информацию, необходимую для создания и настройки компонентов отладчик, используемый для отладки программы изнутри [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладку добавленные усовершенствования, производным от обширной удобство использования, тестирование на предыдущем [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладчики. Можно использовать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки для пошагового выполнения приложения Многоязычная версия, или можно реализовать на лету редактирования переменных при отладке приложения и решения для нескольких языков.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отладка — выполненных вне процесса с отлаживаемой программы, поэтому меньше вмешивается в пространстве процесса приложения. Следовательно проще создавать компоненты, которые взаимодействуют с помощью отладчика не затрагивая отладки программы.  
  
 Чтобы максимально эффективно использовать [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], необходимо ознакомиться со следующими элементами:  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированной среды разработки (IDE)  
  
-   Языка программирования C++  
  
-   ATL COM  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Схема для расширения отладчика](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Описание процесса реализации отладки в ваш продукт, в зависимости от вашего компилятора и его выходные данные.  
  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)  
 Общие сведения о [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладка компонентов, которые включают модуль отладки (DE), средство оценки выражений (EE) и символ обработчик (SH).  
  
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные архитектурные понятия отладки.  
  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)  
 Объясняет, как модуль отладки (DE) действует одновременно в пределах кода, документацию и контекстов вычисления выражения. Описание для каждого из трех контекстов, расположение, положения или оценки, относящиеся к его.  
  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)  
 Содержит ссылки на различные задачи отладки, такие как запуск программы и оценки выражений.