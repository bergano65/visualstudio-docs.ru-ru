---
title: "Интерфейсы службы языка прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 925b504d8cba4813631d4f8ba6f7dbd9750f5eae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-interfaces"></a>Интерфейсы службы языка прежних версий
Для любого конкретного языка программирования одновременно может быть только один экземпляр службы языка. Тем не менее одной языковой службы можно использовать более одного редактора.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Не связывайте языковую службу с любого конкретного редактора. Таким образом при запросе операции службы языка необходимо определить соответствующий редактор как параметр.  
  
## <a name="common-interfaces-associated-with-language-services"></a>Общих интерфейсов, связанных с языковой службы  
 Редактор получает языковой службы, вызывая <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> на соответствующий пакет VSPackage. ИДЕНТИФИКАТОР, переданных в этом вызове службы определяет запрашиваемого языковой службы.  
  
 Для любого количества отдельных классов можно реализовать базовых интерфейсов службы языка. Тем не менее наиболее распространенный подход заключается в том, чтобы реализовать следующие интерфейсы в одном классе:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (необязательно)  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Необходимо реализовать интерфейс на все языковые службы. Он предоставляет сведения о службе языка, например локализованное имя языка, расширения имен файлов, связанных с языковой службы и как извлечь colorizer.  
  
## <a name="additional-language-service-interfaces"></a>Интерфейсы службы дополнительных языков  
 Другие интерфейсы могут быть предоставлены в службе языка. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]запрашивает отдельный экземпляр эти интерфейсы для каждого экземпляра текстового буфера. Таким образом необходимо реализовать каждый из этих интерфейсов в своем объекте. В следующей таблице показаны интерфейсы, которые может потребоваться один экземпляр каждого экземпляра текстового буфера.  
  
|Интерфейс|Описание|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Управляет оформлений окно кода, например раскрывающуюся панель. Этот интерфейс можно получить с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> метод. Имеется один <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> в окне кода.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Окрашивает ключевые слова языка и разделители. Этот интерфейс можно получить с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> метод. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>вызывается во время рисования. Избежать работы с большим объемом вычислений в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> или производительность может снизиться.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Предоставляет подсказки параметров IntelliSense. Если языковая служба распознает символ, которое указывает на данные, метод должен быть отображается, например открывающую скобку, он вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> метод для уведомления текст представление, языковой службы будет готов для отображения всплывающей подсказки Info параметра. Текстовое представление затем выполняет обратный вызов языковой службы, с помощью методов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> интерфейс, чтобы получить сведения, необходимые для отображения всплывающей подсказки.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Предоставляет функции завершения операторов IntelliSense. Если языковая служба готова для отображения списка завершения, он вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод представления текста. Текстовое представление затем выполняет обратный вызов языковой службы, с помощью методов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> объекта.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Позволяет изменять представления текста, с помощью обработчика команд. Класс, можно реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> должны также реализовать интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс. Возвращает текстовое представление <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> объектов с помощью запроса к <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объекта, передаваемого в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод. Должна быть одна <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> для каждого представления.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Перехватывает команд, введенная пользователем в окне кода. Отслеживать выходные данные вашей <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> реализацию, чтобы предоставить сведения о пользовательских завершения и просмотреть изменения<br /><br /> Для передачи вашей <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объект для представления текста, вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|  
  
## <a name="see-also"></a>См. также  
 [Разработке службы языка для прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Контрольный список. Создание языковой службы прежних версий](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)