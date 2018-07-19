---
title: Устаревшие интерфейсы в редакторе | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 867bef2ddf1463005e1d6b0d9ca6c508ede97014
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079511"
---
# <a name="legacy-interfaces-in-the-editor"></a>Устаревшие интерфейсы в редакторе
В редакторе Visual Studio доступны из устаревшие интерфейсы. Пакет SDK для Visual Studio включает адаптеры, известный как *оболочек*, которые поддерживают эти интерфейсы для взаимодействия с новым редактором. Тем не менее рекомендуется обновить устаревший код, чтобы использовать новый редактор API. Ваш код будет демонстрировать лучшие показатели и использовании новых технологий, таких как Windows Presentation Foundation (WPF) и Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Адаптировать устаревшего кода в редакторе](../extensibility/adapting-legacy-code-to-the-editor.md)|Объясняется, как адаптировать код в новый редактор.|  
|[Нового или измененного поведения с помощью редактора адаптеров](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Объясняет, как поведение редактора адаптеров отличается от более ранних версий редактора.|  
|[В редакторе](../extensibility/inside-the-core-editor.md)|Описывает различные компоненты более ранних версиях редактора.|  
|[Создать экземпляр базового редактора с помощью предыдущих версий API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Объясняется, как использовать старый API для создания базового редактора.|  
|[Фабрики редакторов](../extensibility/editor-factories.md)|В этой статье описывается использование фабрик редактора с помощью предыдущих версий API.|  
|[Практическое: регистрация редактор типов файлов](../extensibility/how-to-register-editor-file-types.md)|Объясняется, как связать расширение имени файла в редакторе.|  
|[Пошаговое руководство: Создание основной редактор и регистрация файла тип редактора](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Объясняется, как создать основной редактор и связать расширение имени файла к нему.|  
|[Практическое: предоставить контекст для редакторов](../extensibility/how-to-provide-context-for-editors.md)|Описание способов предоставления контекста для редактора.|  
|[Языковые службы и базовым редактором](../extensibility/language-services-and-the-core-editor.md)|Описание взаимодействия между языковой службы и редактор.|  
|[Доступ к текстового буфера, используя старый API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Объясняется, как получить доступ к текстового буфера, используя старый API.|  
|[Представление theText доступ с помощью предыдущих версий API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Объясняется, как получить доступ к представление текста с помощью предыдущих версий API.|  
|[Настраивать код windows с помощью предыдущих версий API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Объясняется, как настраивать код windows с помощью предыдущих версий API.|  
|[Уровни доступа текста с помощью предыдущих версий API](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Объясняется, как получить доступ к различных уровней текста с помощью предыдущих версий API.|  
|[Использование меток текста с предыдущих версий API](../extensibility/using-text-markers-with-the-legacy-api.md)|Описание способов добавления меток текста с помощью предыдущих версий API.|  
|[Настройка меню и редактор элементов управления с помощью предыдущих версий API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Объясняет, как настраивать элементы управления редактора, используя старый API.|  
|[Управление отмены и повтора с помощью предыдущих версий API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Объясняется, как управлять отмены и повтора с помощью предыдущих версий API.|  
|[Практическое: реализовать найти и заменить механизм](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Объясняется, как управлять поиска и замены с помощью предыдущих версий API.|  
|[Практическое: отключить уведомления об изменении файла](../extensibility/how-to-suppress-file-change-notifications.md)|Объясняется, как отключить уведомления об изменении файла с помощью предыдущих версий API.|  
|[Создание специализированных редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)|В этой статье описывается создание специализированных редакторов и конструкторов.|  
|[Разработка языковой службы прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)|Содержит ссылки на документы о функциях, которые предоставляют возможности настройки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] базовым редактором, добавляя поддержку языковой службы.|  
|[Использовать шрифты и цвета](../extensibility/using-fonts-and-colors.md)|В этой статье описывается использование шрифтов и цветов с устаревшими интерфейсами.|