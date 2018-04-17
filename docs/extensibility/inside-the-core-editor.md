---
title: В редакторе Core | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 95745cbef015e9f6ceddb9b84d75b52ec9805dea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="inside-the-core-editor"></a>В редакторе Core
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Базового редактора — это набор несколько компонентов, которые позволяют изменять и запросов текстовых данных. Если вы настроили базового редактора с помощью предыдущих версий API, могут продолжать использовать эти настройки, которые будет маршрутизироваться с помощью редактора адаптеров. Рекомендуется, однако адаптации настройки новый редактор API.  
  
 Следующие области приведены некоторые важные аспекты базового редактора.  
  
-   Буфер текста  
  
-   Просмотр текста  
  
-   Окно кода  
  
-   Текстовых маркеров:  
  
-   Диспетчер текста  
  
-   Интеграция со службами языка  
  
## <a name="in-this-section"></a>В этом разделе  
 [При создании экземпляра базового редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Пошаговые инструкции о способах использования <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> для создания экземпляра ядро редактора.  
  
 [Доступ к буфер текста с помощью API прежних версий](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Рассматривается роль буфер текста в редакторе core, описание связанных системах, которые используются для доступа к буферу и предоставляет список интерфейсов, реализованных объект текстового буфера <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Текст события буфера в API прежних версий](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Предоставляет список интерфейсов, которые используются для уведомления о событиях буфера текста.  
  
 [Как: регистрация событий буфера текста с помощью API прежних версий](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Описывает, как следует рекомендовать событий текстового буфера.  
  
 [С помощью диспетчера текстов для наблюдения за глобальные параметры](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Описывает использование диспетчера текстов для обмена информацией глобального предпочтений с основными компонентами редактора и получать уведомления о событиях диспетчера текста.  
  
 [Доступ к theText представления с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Описывает роль представления текста в редакторе ядра и список интерфейсов, реализованных <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объекта.  
  
 [Настройка окна кода с помощью API прежних версий](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Сведения о окно кода используется для представления текста заключите, рассматриваются как диспетчер окон кода используется для предоставления оформление на окно кода и предоставляет уведомления о новых представлений.  
  
 [Изменение параметров представления с помощью API прежних версий](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Содержит пошаговые инструкции о принудительно параметры представления и удалите принудительного параметры.  
  
 [Службы языка и базового редактора](../extensibility/language-services-and-the-core-editor.md)  
 Описывает создание экземпляров службы языка для кода оформление элемента управления.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Пошаговое руководство: Создание базового редактора и регистрация файла тип редактора](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Содержит пошаговые инструкции о том, как запустить редактор core из управляемого кода.  
  
 [Раскрывающийся список](../extensibility/drop-down-bar.md)  
 Описывается, как использовать в окне кода раскрывающуюся панель и описываются интерфейсы, которые используются при реализации раскрывающуюся панель.  
  
 [С помощью текстовых маркеров с помощью API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Описание принципов работы текстовых маркеров и как они используются в редакторе ядра и перечислены интерфейсы, которые используются для доступа и управления текстовых маркеров.  
  
 [Как: Добавление маркеров стандартного текста](../extensibility/how-to-add-standard-text-markers.md)  
 Содержит пошаговые инструкции о способах создания текстовая метка и добавление пользовательской команды в контекстном меню.  
  
 [Как: Создание настраиваемых текстовых маркеров](../extensibility/how-to-create-custom-text-markers.md)  
 Предоставляет пошаговые инструкции для создания маркера пользовательский текст и способ указать тип маркера, как служба.