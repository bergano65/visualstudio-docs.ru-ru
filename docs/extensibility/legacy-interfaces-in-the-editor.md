---
title: "Устаревшие интерфейсы в редакторе | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4b437dad35850a20696702b84d8ea98ead8a1e9e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-interfaces-in-the-editor"></a>Устаревшие интерфейсы в редакторе
Чтобы открыть редактор Visual Studio с устаревшими интерфейсами. Пакет SDK для Visual Studio включает адаптеры, известный как *оболочки*, которые поддерживают эти интерфейсы для взаимодействия с новым редактором. Тем не менее рекомендуется обновить устаревший код, чтобы использовать новый редактор API. Код будет более эффективны и могут использовать новые технологии, такие как Windows Presentation Foundation (WPF) и Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Связанные разделы  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Адаптация кода прежних версий в редактор](../extensibility/adapting-legacy-code-to-the-editor.md)|Объясняется, как адаптировать код в новый редактор.|  
|[Нового или измененного поведения с помощью редактора адаптеров](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Объясняет, как поведение редактора адаптеров отличается от более ранних версий редактора.|  
|[В редакторе Core](../extensibility/inside-the-core-editor.md)|Описывает различные компоненты более ранних версиях редактора.|  
|[При создании экземпляра базового редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Объясняется, как использовать устаревший API для создания базового редактора.|  
|[Редактор фабрики](../extensibility/editor-factories.md)|Объясняется, как использовать редактор фабрики с помощью предыдущих версий API.|  
|[Как: регистрация редактор типов файлов](../extensibility/how-to-register-editor-file-types.md)|Объясняется, как связать расширение имени файла с редактором.|  
|[Пошаговое руководство: Создание базового редактора и регистрация файла тип редактора](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Объясняется, как создать ядро редактора и связать его расширение имени файла.|  
|[Как: предоставляют контекст для редакторов](../extensibility/how-to-provide-context-for-editors.md)|Описание способов предоставления контекста для редактора.|  
|[Службы языка и базового редактора](../extensibility/language-services-and-the-core-editor.md)|Описывается взаимодействие между языковой службы и редактор.|  
|[Доступ к буфер текста с помощью API прежних версий](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Описание способов доступа к буферу текста с помощью предыдущих версий API.|  
|[Доступ к theText представления с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Описание способов доступа к представления текста с помощью предыдущих версий API.|  
|[Настройка окна кода с помощью API прежних версий](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Описываются способы настройки windows кода с помощью предыдущих версий API.|  
|[Доступ к слои текста с помощью API прежних версий](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Описание способов доступа к различные уровни текста с помощью предыдущих версий API.|  
|[С помощью текстовых маркеров с помощью API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)|Описание способов добавления текстовых маркеров с помощью предыдущих версий API.|  
|[Настройка меню и редактор элементов управления с помощью API прежних версий](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Объясняется, как настроить редактор элементов управления с помощью предыдущих версий API.|  
|[Управление отмены и повтора, с помощью API прежних версий](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Объясняется, как управлять отмены и повтора с помощью предыдущих версий API.|  
|[Как: реализовать поиск и замена механизм](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Объясняется, как управлять поиска и замены с помощью предыдущих версий API.|  
|[Как: отключить уведомления об изменении файлов](../extensibility/how-to-suppress-file-change-notifications.md)|Объясняется, как отключить уведомления об изменении файлов с помощью предыдущих версий API.|  
|[Создание специализированных редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)|Описание способов создания специальных редакторов и конструкторов.|  
|[Разработка языковой службы прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)|Содержит ссылки на документы, посвященные функции, которые обеспечивают возможности настройки в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] базового редактора, добавляя поддержку языковой службы.|  
|[Шрифты и цвета](../extensibility/using-fonts-and-colors.md)|Описание способов использования шрифты и цвета с устаревшими интерфейсами.|