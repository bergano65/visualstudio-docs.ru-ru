---
title: "Приступая к работе с расширения отладчика | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 258fcfcc97d0a6b1455ec60201527cde3e87f9b8
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-debugger-extensibility"></a>Приступая к работе с расширения отладчика
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Сведения, необходимые для создания и настройки компонентов отладчик для отладки программы с помощью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Отладка добавлены усовершенствования, производным от обширные удобство использования тестированию на предыдущем [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладчики. Можно использовать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отладка в процессе приложения многоязыкового интерфейса, или можно реализовать на лету редактирование переменных при отладке приложений и решений для нескольких языков.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Отладка является выполненного out-of-process с отлаживаемой программы и, следовательно, меньше вмешивается в пространстве процесса приложения. Следовательно проще создавать компоненты, которые взаимодействуют с отладчиком не затрагивая отладки программы.  
  
 Лучше использовать [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], следует ознакомиться со следующим:  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированной среды разработки (IDE)  
  
-   Язык программирования C++  
  
-   ATL COM  
  
## <a name="in-this-section"></a>Содержание  
 [Схема для расширения отладчика](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Описание процесса реализации продукта, в зависимости от вашего компилятора и его выходные данные отладки.  
  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)  
 Общие сведения о [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладка компонентов, которые включают отладчик (DE), средство оценки выражений (EE) и обработчик символ (SH).  
  
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные архитектурные понятия отладки.  
  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)  
 Объясняет, как отладчик (DE) одновременно работает в пределах кода, документацию и контекстов выражения вычислений. Описание для каждого из трех контекстов, расположение, положение или оценки, относящиеся к нему.  
  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)  
 Содержит ссылки на различные задачи отладки, такие как запуск программы и оценки выражений.
