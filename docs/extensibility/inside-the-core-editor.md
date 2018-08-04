---
title: Внутри основной редактор | Документация Майкрософт
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
ms.openlocfilehash: 37c62ebad5b5f119c9acf5b62b14db6743949c19
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500453"
---
# <a name="inside-the-core-editor"></a>В редакторе
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Базовый редактор — это набор из нескольких компонентов, которые позволяют изменять и запрашивать текстовую информацию. Если вы настраивали базовый редактор, используя старый API, могут продолжать использовать эти настройки, которые будут направляться через редактора адаптеров. Рекомендуется, однако адаптации настройки в новый редактор API.  
  
 Следующие области приведены некоторые важные аспекты базовым редактором.  
  
-   Текстовый буфер  
  
-   Представление текста  
  
-   Окно кода  
  
-   Текстовые метки  
  
-   Диспетчер текста  
  
-   Интеграция со службами языка  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Создать экземпляр базового редактора с помощью предыдущих версий API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Содержит пошаговые инструкции о том, как использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> для создания экземпляра ядра редактора.  
  
 [Доступ к текстового буфера, используя старый API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Рассматривается роль текстового буфера в базовом редакторе, объясняет связанных системах, которые используются для доступа к буферу и предоставляет список интерфейсов, реализованных в объект текстового буфера, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Событий текстового буфера, старый API](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Список интерфейсов, которые используются для уведомления о событиях буфера текста.  
  
 [Практическое: регистрировать события буфера текста с старый API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 В этой статье описывается уведомить событий текстового буфера.  
  
 [Использование диспетчера текстов для наблюдения за глобальные параметры](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Описывает использование диспетчера текстов для глобального предпочтений совместная работа с основными компонентами редактора и для получения уведомлений о событиях диспетчера текста.  
  
 [Представление theText доступ с помощью предыдущих версий API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Описывает роль представления текста в редакторе и список интерфейсов, реализованных <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объекта.  
  
 [Настраивать код windows с помощью предыдущих версий API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Сведения о окно кода используется для заключения в них представление текста, обсуждается, как диспетчер окон кода используется для предоставления оформление в окно кода и предоставляет уведомления о новых представлений.  
  
 [Изменение параметров представления с помощью предыдущих версий API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Содержит пошаговые инструкции о принудительный Просмотр параметров и как удалить принудительные параметры.  
  
 [Языковые службы и базовым редактором](../extensibility/language-services-and-the-core-editor.md)  
 Описывает создание экземпляров языковой службы для оформления кода элемента управления.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Пошаговое руководство: Создание базового редактора и регистрации файла тип редактора](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Содержит пошаговые инструкции о том, как запустить редактор core из управляемого кода.  
  
 [Раскрывающийся список](../extensibility/drop-down-bar.md)  
 Описывается, как используется в окне кода раскрывающуюся панель и описываются интерфейсы, которые используются при реализации раскрывающейся панелью.  
  
 [Использование меток текста с предыдущих версий API](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Поясняет понятие текстовые метки и как они используются в базовом редакторе и перечислены интерфейсы, которые используются для доступа и управления текстовых маркеров.  
  
 [Практическое: Добавление стандартные текстовые метки](../extensibility/how-to-add-standard-text-markers.md)  
 Содержит пошаговые инструкции о способах создания текстового маркера и добавление пользовательской команды в контекстное меню.  
  
 [Практическое: Создание настраиваемых текстовых маркеров](../extensibility/how-to-create-custom-text-markers.md)  
 Содержит пошаговые инструкции о том, как создать пользовательский текстовый маркер и обеспечить тип маркера как услуга.