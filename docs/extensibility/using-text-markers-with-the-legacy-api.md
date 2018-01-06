---
title: "С помощью текстовых маркеров с помощью прежних версий API | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 98c889bc1bc128a941f726348781a633799475de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="using-text-markers-with-the-legacy-api"></a>С помощью текстовых маркеров с помощью API прежних версий
Текстовая метка — с плавающей запятой диапазон текста в буфере, который может повлиять на отображение и поведение области текста. Маркеры включают точки останова, закладки, подчеркивание волнистой линией и только для чтения областей. По сути текстовых маркеров отличаются от Цветовая подсветка синтаксиса. Цветовая подсветка синтаксиса — быстрый способ передачи синтаксис, связанный с областью текста. Цветовая подсветка синтаксиса обычно запрашивается, когда Windows перерисовывает экрана, когда важна скорость. Цветовая подсветка синтаксиса изменяет цвет текста. Текст метки можно изменить многие другие свойства текста. Можно «float» и применить специальное поведение текстовых маркеров: выделение цветом.  
  
 Из-за снижение производительности, связанные с маркерами текста не следует создавать много маркеры для буферов текста. Каждый маркер обновляется каждый раз, что пользователь изменяет содержимое буфера.  
  
> [!NOTE]
>  Пользователи могут изменять цвет тип видимым маркера, но не его форма и стиль. Дополнительные сведения см. в разделе [шрифты и цвета, среда, диалоговое окно «Параметры»](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Как: Добавление маркеров стандартного текста](../extensibility/how-to-add-standard-text-markers.md)|Описание процедуры добавления стандартного текста тип маркера, предоставляемых [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] базового редактора для представления текста.|  
|[Как: реализовать маркеры ошибки](../extensibility/how-to-implement-error-markers.md)|Описывает, как реализовать экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] маркер, который используется для указания ошибок с помощью красными волнистыми линиями.|  
|[Как: Создание настраиваемых текстовых маркеров](../extensibility/how-to-create-custom-text-markers.md)|Описывает, как создать и добавить настраиваемый текст тип маркера для представления текста.|  
|[Как: использовать маркеры текста](../extensibility/how-to-use-text-markers.md)|Описание способов добавления текстовых маркеров.|  
|[В редакторе Core](../extensibility/inside-the-core-editor.md)|Описание возможностей базового редактора и подробные сведения о настройке базового редактора.|  
|[Возможности редактора](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Описание функций, доступных в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] базового редактора.|  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Универсальный механизм для получения сведений о конкретных текстового типа маркера, предопределенных редактором или зарегистрированные пакетом VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Предоставляет доступ к и регулирует положение текстовая метка в буфер текста с помощью двумерные координаты.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Предоставляет методы для управления текстовых маркеров.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Предоставляет обратные вызовы для [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки и другие процессы, которые используются для настройки текстовой метки.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Расширяет функциональность, которая доступна через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейса, предоставляя дополнительные обратные вызовы.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Расширяет функциональность, которая доступна через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейса, предоставляя дополнительные обратные вызовы.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Включает тип маркера для определения того, используют ли другие типы маркеров тот же набор цветов.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Предоставляет контекст для текстовых маркеров базового редактора. Для каждого типа маркера текст, который является базового редактора, IDE создает отдельную <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> объекта.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Обработчик, который предоставляется для которого глифы поддерживает редактирование и перетащите маркеры. Глиф — значок, указывающий на позицию маркер.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Возвращает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> интерфейс из службы, которая содержит текст маркеров для других пакетов VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Предоставляет доступ к и изменяет положение текстовая метка в буфер текста с использованием одномерный массив координат. Если это возможно, не следует использовать данный интерфейс.