---
title: "С помощью текстовых маркеров с API прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - текстовых меток"
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# С помощью текстовых маркеров с API прежних версий
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Метка текст перемещаемые диапазон текста в буфере, который может повлиять на отображение и расширения функциональности области текста.  Метки включают точки останова, закладки, волнистые подчеркивание и только для чтения области.  По сути, расцветка метки текста отличается от синтаксиса.  Расцветка синтаксиса быстрый способ передачи синтаксис языка, связанного с областью текста.  Расцветка синтаксиса обычно запрашивается, когда окна обновить экран, если скорость имеет значения.  Расцветка синтаксиса изменяет только цвет текста.  Текст метки могут изменять многие другие свойства текста.  Отправьте СМС метки законсервируйте "float" и применить специальные расширения функциональности и расцветка.  
  
 Вследствие снижения производительности, связанного с метками текст, не создайте несколько меток для текстовых буферов.  Каждая метка обновляется каждый раз, когда пользователь изменяет содержимое буфера.  
  
> [!NOTE]
>  Пользователи могут изменять цвет видимого только тип маркера не ее форму и стиль.  Дополнительные сведения см. в разделе [Страница "Шрифты и цвета", папка "Среда", диалоговое окно "Параметры"](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## Связанные разделы  
  
|Заголовок|Описание|  
|---------------|--------------|  
|[Практическое руководство: Добавление маркеров стандартный текст](../extensibility/how-to-add-standard-text-markers.md)|Описывает, как добавлять стандартный тип маркера текст, предоставляемый [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] редактор core к представлению текста.|  
|[Практическое руководство: реализации маркеры ошибки](../extensibility/how-to-implement-error-markers.md)|Описывает, как реализовать экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] метка, используемая для отображения ошибок с помощью волнистого красное подчеркивание.|  
|[Практическое руководство: Создание пользовательского текста маркеры](../extensibility/how-to-create-custom-text-markers.md)|Описывает, как создать и добавить пользовательский тип маркера текста к представлению текста.|  
|[Практическое руководство: использование текстовых меток](../extensibility/how-to-use-text-markers.md)|Объясняет, как добавить метки текста.|  
|[В редакторе ядра](../extensibility/inside-the-core-editor.md)|Описывает основные функции редактора и предоставляет сведения о том, как настраивать редактор.|  
|[Editor Features](http://msdn.microsoft.com/ru-ru/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Описывает функции, доступные в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] редактор.|  
  
## Ссылки  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Универсального механизма для получения сведений о конкретном типе маркера текст, предоставляет ли предопределен редактором или зарегистрирован VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Предоставляет доступ к и корректирует положение метки текста в текстовом буфере с помощью плоских координат.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Предоставляет методы для управления текстовой метки.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Предоставляет обратные вызовы [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Интегрированная среда разработки и другие процессы, которые используются для обработки метку текста.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Расширяющий функциональность, доступную через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс, предоставив новые обратные вызовы.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Расширяющий функциональность, доступную через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс, предоставив новые обратные вызовы.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Разрешает тип маркера для указания используют ли другие типы маркеров тот же набор цветов.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Предоставляет контекст для меток текста в редакторе.  Для каждого типа маркера текста, в редакторе, интегрированная среда разработки создает отдельное <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> объект.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Обработчик, который указан для меток глифы, поддерживающие изменение перетаскивания.  Глиф значок, который указывает положение метки.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Возвращает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> интерфейс из службы, которая предоставляет текстовой метки другое VSPackages.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Предоставляет доступ к и корректирует положение метки текста в текстовом буфере с помощью одномерных координат.  Если возможно, не используйте этот интерфейс.