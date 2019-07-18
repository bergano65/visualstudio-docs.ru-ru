---
title: Устаревшие интерфейсы в редакторе | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8483068ae03c9a57fc67b528393e5d6830c3ec33
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180293"
---
# <a name="legacy-interfaces-in-the-editor"></a>Интерфейсы прежних версий в редакторе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В редакторе Visual Studio доступны из устаревшие интерфейсы. Пакет SDK для Visual Studio включает адаптеры, известный как *оболочек*, которые поддерживают эти интерфейсы для взаимодействия с новым редактором. Тем не менее рекомендуется обновить устаревший код, чтобы использовать новый редактор API. Ваш код будет демонстрировать лучшие показатели и использовании новых технологий, таких как Windows Presentation Foundation (WPF) и Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Адаптация кода прежних версий для редактора](../extensibility/adapting-legacy-code-to-the-editor.md)|Объясняется, как адаптировать код в новый редактор.|  
|[Новое или измененное поведение с адаптерами редактора](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Объясняет, как поведение редактора адаптеров отличается от более ранних версий редактора.|  
|[Компоненты основного редактора](../extensibility/inside-the-core-editor.md)|Описывает различные компоненты более ранних версиях редактора.|  
|[Создание экземпляра основного редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Объясняется, как использовать старый API для создания базового редактора.|  
|[Фабрики редактора](../extensibility/editor-factories.md)|В этой статье описывается использование фабрик редактора с помощью предыдущих версий API.|  
|[Практическое руководство. Регистрация типов файлов в редакторе](../extensibility/how-to-register-editor-file-types.md)|Объясняется, как связать расширение имени файла в редакторе.|  
|[Пошаговое руководство: создание основного редактора и регистрация типов файлов в редакторе](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Объясняется, как создать основной редактор и связать расширение имени файла к нему.|  
|[Практическое руководство. Предоставление контекста для редакторов](../extensibility/how-to-provide-context-for-editors.md)|Описание способов предоставления контекста для редактора.|  
|[Языковые службы и основной редактор](../extensibility/language-services-and-the-core-editor.md)|Описание взаимодействия между языковой службы и редактор.|  
|[Доступ к текстовому буферу с помощью API прежних версий](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Объясняется, как получить доступ к текстового буфера, используя старый API.|  
|[Доступ к текстовому представлению с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Объясняется, как получить доступ к представление текста с помощью предыдущих версий API.|  
|[Настройка кода Windows с помощью API прежних версий](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Объясняется, как настраивать код windows с помощью предыдущих версий API.|  
|[Доступ к слоям текста с помощью API прежних версий](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Объясняется, как получить доступ к различных уровней текста с помощью предыдущих версий API.|  
|[Использование текстовых маркеров с помощью API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)|Описание способов добавления меток текста с помощью предыдущих версий API.|  
|[Настройка меню и элементов управления редактора с помощью API прежних версий](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Объясняет, как настраивать элементы управления редактора, используя старый API.|  
|[Управление отмены и повтора с помощью API прежних версий](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Объясняется, как управлять отмены и повтора с помощью предыдущих версий API.|  
|[Практическое руководство. Реализация механизма поиска и замены](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Объясняется, как управлять поиска и замены с помощью предыдущих версий API.|  
|[Практическое руководство. Отключение уведомлений об изменении файла](../extensibility/how-to-suppress-file-change-notifications.md)|Объясняется, как отключить уведомления об изменении файла с помощью предыдущих версий API.|  
|[Создание специализированных редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)|В этой статье описывается создание специализированных редакторов и конструкторов.|  
|[Разработка языковой службы прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)|Содержит ссылки на документы о функциях, которые предоставляют возможности настройки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] базовым редактором, добавляя поддержку языковой службы.|  
|[Использование шрифтов и цветов](../extensibility/using-fonts-and-colors.md)|В этой статье описывается использование шрифтов и цветов с устаревшими интерфейсами.|
