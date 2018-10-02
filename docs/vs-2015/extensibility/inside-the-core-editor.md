---
title: Внутри основной редактор | Документация Майкрософт
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
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2d9ec83c700f9166dc6b73860547bcacd265a15
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561735"
---
# <a name="inside-the-core-editor"></a>В редакторе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [внутри основной редактор](https://docs.microsoft.com/visualstudio/extensibility/inside-the-core-editor).  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Базовый редактор — это набор из нескольких компонентов, которые позволяют изменять и запрашивать текстовую информацию. Если вы настраивали базовый редактор, используя старый API, могут продолжать использовать эти настройки, которые будут направляться через редактора адаптеров. Рекомендуется, однако адаптации настройки в новый редактор API.  
  
 Следующие области приведены некоторые важные аспекты базовым редактором.  
  
-   Текстовый буфер  
  
-   Представление текста  
  
-   Окно кода  
  
-   Текстовые метки  
  
-   Диспетчер текста  
  
-   Интеграция со службами языка  
  
## <a name="in-this-section"></a>В этом разделе  
 [Создание экземпляра основного редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Содержит пошаговые инструкции о том, как использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> для создания экземпляра ядра редактора.  
  
 [Доступ к текстовому буферу с помощью API прежних версий](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Рассматривается роль текстового буфера в базовом редакторе, объясняет связанных системах, которые используются для доступа к буферу и предоставляет список интерфейсов, реализованных в объект текстового буфера, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [События текстового буфера в интерфейсе API прежних версий](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Список интерфейсов, которые используются для уведомления о событиях буфера текста.  
  
 [Практическое руководство. Регистрация событий текстового буфера с помощью API прежних версий](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 В этой статье описывается уведомить событий текстового буфера.  
  
 [Использование диспетчера текстов для мониторинга глобальных параметров](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Описывает использование диспетчера текстов для глобального предпочтений совместная работа с основными компонентами редактора и для получения уведомлений о событиях диспетчера текста.  
  
 [Доступ к текстовому представлению с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Описывает роль представления текста в редакторе и список интерфейсов, реализованных <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объекта.  
  
 [Настройка кода Windows с помощью API прежних версий](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Сведения о окно кода используется для заключения в них представление текста, обсуждается, как диспетчер окон кода используется для предоставления оформление в окно кода и предоставляет уведомления о новых представлений.  
  
 [Изменение параметров представления с помощью API прежних версий](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Содержит пошаговые инструкции о принудительный Просмотр параметров и как удалить принудительные параметры.  
  
 [Языковые службы и основной редактор](../extensibility/language-services-and-the-core-editor.md)  
 Описывает создание экземпляров языковой службы для оформления кода элемента управления.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Пошаговое руководство. Создание основного редактора и регистрация типов файлов в редакторе](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Содержит пошаговые инструкции о том, как запустить редактор core из управляемого кода.  
  
 [Раскрывающаяся панель](../extensibility/drop-down-bar.md)  
 Описывается, как используется в окне кода раскрывающуюся панель и описываются интерфейсы, которые используются при реализации раскрывающейся панелью.  
  
 [Использование текстовых маркеров с помощью API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Поясняет понятие текстовые метки и как они используются в базовом редакторе и перечислены интерфейсы, которые используются для доступа и управления текстовых маркеров.  
  
 [Практическое руководство. Добавление стандартных текстовых маркеров](../extensibility/how-to-add-standard-text-markers.md)  
 Содержит пошаговые инструкции о способах создания текстового маркера и добавление пользовательской команды в контекстное меню.  
  
 [Практическое руководство. Создание пользовательских текстовых маркеров](../extensibility/how-to-create-custom-text-markers.md)  
 Содержит пошаговые инструкции о том, как создать пользовательский текстовый маркер и обеспечить тип маркера как услуга.

