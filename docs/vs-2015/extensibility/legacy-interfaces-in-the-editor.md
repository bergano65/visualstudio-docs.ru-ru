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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180293"
---
# <a name="legacy-interfaces-in-the-editor"></a>Интерфейсы прежних версий в редакторе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Доступ к редактору Visual Studio можно получить из устаревших интерфейсов. Пакет SDK для Visual Studio включает адаптеры, называемые *оболочками совместимости*, которые позволяют этим интерфейсам взаимодействовать с новым редактором. Тем не менее рекомендуется обновить устаревший код, чтобы использовать новый API редактора. Код будет работать лучше, и вы сможете использовать новые технологии, такие как Windows Presentation Foundation (WPF) и Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Адаптация кода прежних версий для редактора](../extensibility/adapting-legacy-code-to-the-editor.md)|Описывается способ адаптации кода к новому редактору.|  
|[Новое или измененное поведение с адаптерами редактора](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Описание отличий поведения адаптеров редактора от предыдущих версий редактора.|  
|[Компоненты основного редактора](../extensibility/inside-the-core-editor.md)|Описание различных компонентов более ранних версий редактора.|  
|[Создание экземпляра основного редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Объясняется, как использовать устаревший API для создания экземпляра базового редактора.|  
|[Фабрики редактора](../extensibility/editor-factories.md)|Объясняется, как использовать фабрики редактора с устаревшим API.|  
|[Практическое руководство. Регистрация типов файлов в редакторе](../extensibility/how-to-register-editor-file-types.md)|Объясняется, как связать расширение имени файла с редактором.|  
|[Пошаговое руководство. Создание основного редактора и регистрация типов файлов в редакторе](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Объясняется, как создать основной редактор и связать с ним расширение имени файла.|  
|[Практическое руководство. Предоставление контекста для редакторов](../extensibility/how-to-provide-context-for-editors.md)|Описание способов предоставления контекста для редактора.|  
|[Языковые службы и основной редактор](../extensibility/language-services-and-the-core-editor.md)|Объясняет взаимодействие между языковой службой и редактором.|  
|[Доступ к текстовому буферу с помощью API прежних версий](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Объясняет, как получить доступ к текстовому буферу с помощью API прежних версий.|  
|[Доступ к текстовому представлению с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Объясняет, как получить доступ к текстовому представлению с помощью API прежних версий.|  
|[Настройка кода Windows с помощью API прежних версий](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Объясняет, как настроить окна кода с помощью API прежних версий.|  
|[Доступ к слоям текста с помощью API прежних версий](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Объясняет, как получить доступ к различным слоям текста с помощью API прежних версий.|  
|[Использование текстовых маркеров с помощью API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)|Объясняет, как добавлять текстовые маркеры с помощью API прежних версий.|  
|[Настройка меню и элементов управления редактора с помощью API прежних версий](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Объясняет, как настроить элементы управления редактора с помощью API прежних версий.|  
|[Управление отмены и повтора с помощью API прежних версий](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Объясняется, как управлять отменой и повтором с помощью API прежних версий.|  
|[Практическое руководство. Реализация механизма поиска и замены](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Объясняется, как управлять поиском и заменой с помощью устаревшего API.|  
|[Практическое руководство. Отключение уведомлений об изменении файла](../extensibility/how-to-suppress-file-change-notifications.md)|Объясняет, как отключить уведомления об изменении файлов с помощью API прежних версий.|  
|[Создание специализированных редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)|Описывает создание пользовательских редакторов и конструкторов.|  
|[Разработка языковой службы прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)|Содержит ссылки на документы о функциях, которые предоставляют возможности настройки для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] основного редактора, путем добавления поддержки языковой службы.|  
|[Использование шрифтов и цветов](../extensibility/using-fonts-and-colors.md)|Объясняется, как использовать шрифты и цвета с устаревшими интерфейсами.|
