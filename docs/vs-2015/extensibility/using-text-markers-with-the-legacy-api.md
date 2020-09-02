---
title: Использование текстовых маркеров с устаревшим API | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dff5e6ecf60d389730841e99b87db584465e020
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695480"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Использование текстовых маркеров с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Текстовый маркер — это плавающий фрагмент текста в буфере, который может повлиять на отображение и поведение области текста. Маркеры включают точки останова, закладки, волнистые линии и регионы только для чтения. Текстовые маркеры по сути отличаются от цветов синтаксиса. Цветовое выделение синтаксиса — это быстрый способ связи с синтаксисом языка, связанным с областью текста. Выделение синтаксиса обычно запрашивается, когда Windows перерисовывает экран, когда важна скорость. При цветовом синтаксисе изменяется только цвет текста. Текстовые маркеры могут изменять многие другие свойства текста. Текстовые маркеры могут иметь значение "Float" и применять специальное поведение и цвета.  
  
 Из-за затрат на производительность, связанных с текстовыми маркерами, не создавайте много маркеров для текстовых буферов. Каждый маркер обновляется каждый раз, когда пользователь редактирует содержимое буфера.  
  
> [!NOTE]
> Пользователи могут изменять цвет видимого типа маркера, но не его форму и стиль. Дополнительные сведения см. в разделе [шрифты и цвета, среда, диалоговое окно Параметры](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Практическое руководство. Добавление стандартных текстовых маркеров](../extensibility/how-to-add-standard-text-markers.md)|Описывает, как добавить стандартный тип текстового маркера, предоставленный [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] основным редактором, в текстовое представление.|  
|[Практическое руководство. Реализация маркеров ошибок](../extensibility/how-to-implement-error-markers.md)|Описывает, как реализовать экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] маркера, который используется для обозначения ошибок с помощью красной волнистой линией.|  
|[Практическое руководство. Создание пользовательских текстовых маркеров](../extensibility/how-to-create-custom-text-markers.md)|Описывает создание и Добавление пользовательского типа маркера текста в текстовое представление.|  
|[Практическое руководство. Использование текстовых маркеров](../extensibility/how-to-use-text-markers.md)|Объясняет, как добавлять текстовые маркеры.|  
|[Компоненты основного редактора](../extensibility/inside-the-core-editor.md)|Описание возможностей основного редактора и сведения о настройке основного редактора.|  
|[Функции редактора](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Описание функций, доступных в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] основном редакторе.|  
  
## <a name="reference"></a>Справочник  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Предоставляет единый механизм для получения сведений о конкретном типе текстового маркера, будь то предопределенный редактор или зарегистрированный пакетом VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Предоставляет доступ и корректирует расположение текстового маркера в текстовом буфере с помощью двумерных координат.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Предоставляет методы для управления текстовыми маркерами.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Предоставляет обратные вызовы для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] интегрированной среды разработки и других процессов, которые используются для корректировки текстового маркера.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Расширяет функциональные возможности, доступные через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс, предоставляя дополнительные обратные вызовы.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Расширяет функциональные возможности, доступные через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс, предоставляя дополнительные обратные вызовы.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Включает тип маркера, чтобы определить, используют ли другие типы маркеров одинаковый набор цветов.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Предоставляет контекст для меток текста в редакторе. Для каждого типа текстового маркера, который находится в основном редакторе, интегрированная среда разработки создает отдельный <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> объект.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Обработчик, который предоставляется для маркеров, глифы которых поддерживают редактирование с помощью перетаскивания. Глиф — это значок, указывающий на расположение маркера.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Возвращает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> интерфейс из службы, предоставляющей текстовые маркеры другим пакетам VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Предоставляет доступ и корректирует расположение текстового маркера в текстовом буфере с помощью одномерных координат. Если возможно, не используйте этот интерфейс.
