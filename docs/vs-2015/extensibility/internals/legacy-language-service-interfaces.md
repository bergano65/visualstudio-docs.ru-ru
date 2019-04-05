---
title: Интерфейсы службы прежней версией языка | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 02f63cd5e3f0599723aee12f7aed2c56b74c3249
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993293"
---
# <a name="legacy-language-service-interfaces"></a>Интерфейсы языковой службы прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Для любого конкретного языка программирования и одновременно может быть только один экземпляр службы языка. Тем не менее одной языковой службы может обслуживать несколько редакторов.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] связывает языковую службу с любого конкретного редактора. Таким образом при запросе операции службы языка, необходимо определить соответствующий редактор как параметр.  
  
## <a name="common-interfaces-associated-with-language-services"></a>Общие интерфейсы, связанные со службами языка  
 Редактор получает языковой службы, вызывая <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> на соответствующий пакет VSPackage. ИДЕНТИФИКАТОР, переданных в этом вызове службы определяет запрашиваемой службы языка.  
  
 Службы языка базовых интерфейсов можно реализовать на любом количестве отдельные классы. Тем не менее наиболее распространенный подход заключается в том, чтобы реализовать следующие интерфейсы в одном классе:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (необязательно)  
  
  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Интерфейс должен быть реализован на любые службы языка. Он предоставляет сведения о службе языка, такие как локализованное имя языка, расширения имен файлов, связанных с языковой службы и как получить палитры.  
  
## <a name="additional-language-service-interfaces"></a>Интерфейсы служб дополнительных языков  
 Другие интерфейсы можно предоставить службе языка. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] запрашивает отдельный экземпляр этих интерфейсов для каждого экземпляра текстового буфера. Таким образом необходимо реализовать каждый из этих интерфейсов на свой собственный объект. В следующей таблице показаны интерфейсы, которые требуется один экземпляр каждого экземпляра текстового буфера.  
  
|Интерфейс|Описание|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Управляет окна кода элементы оформления, например раскрывающейся панелью. Этот интерфейс можно получить с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> метод. Имеется один <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> каждого окна кода.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Окрашивает ключевые слова языка и разделители. Этот интерфейс можно получить с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> метод. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> вызывается во время рисования. Избегайте большого количества вычислений работы внутри <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> или может наблюдаться снижение производительности.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Предоставляет параметр подсказок IntelliSense. Когда служба языка распознает символ, который указывает на данные, метод должен быть отображения, например открывающей круглой скобкой, он вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> метод для уведомления текст view, языковая служба готова для отображения в подсказке сведений о параметрах. Представление текста затем выполняет обратный вызов языковой службы с помощью методов класса <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> интерфейс, чтобы получить сведения, необходимые для отображения всплывающей подсказки.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Обеспечивает завершение операторов IntelliSense. Когда служба языка будет готов для отображения списка завершения, он вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод для представления текста. Представление текста затем выполняет обратный вызов языковой службы, с помощью методов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> объекта.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Позволяет изменять представления текста, с помощью обработчика команды. Класс, в которой выполнять <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> также должен реализовать интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс. Получает представление текста <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> объекта, запросив <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объект, передаваемый в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод. Должен быть один <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> для каждого представления.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Перехватывание команд, который пользователь вводит в окно кода. Отслеживать выходные данные из вашей <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> реализации для предоставления специальных завершений информации и просмотреть изменения<br /><br /> Для передачи в <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объект для представления текста, вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|  
  
## <a name="see-also"></a>См. также  
 [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Контрольный список: Создание языковой службы прежних версий](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
