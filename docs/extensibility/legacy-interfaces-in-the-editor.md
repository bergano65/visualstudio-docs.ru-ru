---
title: "Устаревшие интерфейсы в редакторе | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 10
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
ms.openlocfilehash: e6f4c118ac9306bc533ba7cf62037a8255e9c42f
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-interfaces-in-the-editor"></a>Устаревшие интерфейсы в редакторе
Чтобы открыть редактор Visual Studio с устаревшими интерфейсами. Пакет SDK для Visual Studio включает адаптеры, известный как *оболочки*, которые поддерживают эти интерфейсы для взаимодействия с новым редактором. Тем не менее рекомендуется обновить устаревший код с помощью редактора новый API. Код работает наилучшим образом, и можно использовать новые технологии, такие как Windows Presentation Foundation (WPF) и Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Связанные разделы  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Адаптация кода прежних версий для редактора](../extensibility/adapting-legacy-code-to-the-editor.md)|Объясняется, как адаптировать код в новый редактор.|  
|[Нового или измененного поведения с помощью редактора адаптеров](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Объясняет, как поведение редактора адаптеров отличается от более ранних версий редактора.|  
|[В редакторе ядра](../extensibility/inside-the-core-editor.md)|Описание различных компонентов более ранних версиях редактора.|  
|[Создание базового редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Объясняется, как использовать старый API для создания базового редактора.|  
|[Редактор фабрик](../extensibility/editor-factories.md)|Объясняется, как использовать редактор фабрики с API прежних версий.|  
|[Практическое руководство: регистрация редактор типов файлов](../extensibility/how-to-register-editor-file-types.md)|Объясняется, как связать расширение имени файла для редактора.|  
|[Пошаговое руководство: Создание базового редактора и регистрация файла тип редактора](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Объясняется, как создать основной редактор и связать его расширение имени файла.|  
|[Практическое руководство: предоставляют контекст для редакторов](../extensibility/how-to-provide-context-for-editors.md)|Описание способов предоставления контекста для редактора.|  
|[Языковые службы и базовый редактор](../extensibility/language-services-and-the-core-editor.md)|Описание взаимодействия между языковую службу и редактор.|  
|[Доступ к текстовый буфер с помощью API прежних версий](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Описание способов доступа к буферу текста с помощью API прежних версий.|  
|[Доступ к theText представление с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Описание способов доступа к представление текста с помощью API прежних версий.|  
|[Настройка кода Windows с помощью API прежних версий](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Описание способов настройки windows кода с помощью API прежних версий.|  
|[Доступ к текстовые слои с помощью API прежних версий](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Описание способов доступа к различным уровням элемента текста с помощью API прежних версий.|  
|[С помощью текстовых маркеров с API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)|Описание способов добавления текстовых меток с помощью API прежних версий.|  
|[Настройка меню и элементы управления редактора с помощью API прежних версий](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Объясняется, как настроить элементы управления редактора с помощью API прежних версий.|  
|[Управление отмены и повтора с помощью API прежних версий](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Объясняется, как управлять отмены и повтора с помощью API прежних версий.|  
|[Практическое руководство: реализации поиска и замены механизм](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Объясняется, как управлять поиска и замены с помощью API прежних версий.|  
|[Практическое руководство: отключение уведомлений об изменении файлов](../extensibility/how-to-suppress-file-change-notifications.md)|Объясняет, как отключить уведомления об изменении файлов с помощью API прежних версий.|  
|[Создание пользовательские редакторы и конструкторы](../extensibility/creating-custom-editors-and-designers.md)|Объясняется, как создавать пользовательские редакторы и конструкторы.|  
|[Разработка языковую службу для прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)|Ссылки на документы о функциях, которые обеспечивают возможности настройки для [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] базового редактора, добавляя поддержку языковой службы.|  
|[Шрифты и цвета](../extensibility/using-fonts-and-colors.md)|Описание способов использования с устаревшими интерфейсами, шрифты и цвета.|
