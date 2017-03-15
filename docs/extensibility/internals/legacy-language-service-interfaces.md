---
title: "Интерфейсы службы языка прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IVsLanguageInfo"
  - "языковые службы, объекты"
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Интерфейсы службы языка прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Для любого языка программирования может существовать только один экземпляр службы языка одновременно.  Однако одна служба языка может обслуживать несколько редактор.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] не связывает службу языка с одним конкретным редактором.  Поэтому при запросе операции службы языка необходимо указать соответствующий редактор в качестве параметра.  
  
## Общие интерфейсы, связанные со службами языка  
 Редактор получает путем вызова службы языка <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> на соответствующем VSPackage.  Идентификатор службы \(sid\), передаваемое в этот вызов определяет службу языка запрошено.  
  
 Можно реализовать интерфейсы службы языка в любом количестве различных базовых классов.  Однако общий подход реализовывать следующие интерфейсы в одном классе.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> \(необязательный параметр\)  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейс должен быть реализован во всех службах языка.  Он предоставляет сведения о службе языка, например локализованное имя языка расширения имени файла, связанные со службой языка и как получить colorizer.  
  
## Дополнительные интерфейсы службы языка  
 Другие интерфейсы могут быть защищены с этой службой языка.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запрашивает отдельный экземпляр этих интерфейсов для каждого экземпляра текстового буфера.  Поэтому необходимо реализовать каждый из этих интерфейсов в собственном объекте.  В следующей таблице перечислены интерфейсы, требующих одного экземпляра для каждого экземпляра текстового буфера.  
  
|Интерфейс|Описание|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Управляет оформления окна, например панель кода раскрывающемся списке.  Можно получить этот интерфейс с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> метод.  Одно <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> в поле кода.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Ключевые слова языка Colorizes и разделители.  Можно получить этот интерфейс с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> метод.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> вызывается во время рисования.  Избегайте вычислени\-интенсивнейший работы внутри <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> или производительность может снизиться.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Предоставляет подсказки параметров IntelliSense.  Когда служба языка распознает символ, указывающий, что данные метода должны отображаться в открытую круглую скобку, она вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> метод, чтобы уведомить представление текста, что служба языка готова указать подсказку сведения о параметрах.  Представление текста, после чего вызывает обратно в службу языка, используя методы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> интерфейс для получения необходимых сведений указать подсказку.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Предоставляет завершение выписки IntelliSense.  Когда служба готова для отображения списка завершения языка, он вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод представления текста.  Представление текста, после чего вызывает обратно в службу языка с помощью методов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> объект.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Разрешает для изменения представления текста с помощью обработчика команды.  Класс, в котором реализуется <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> также должен реализовывать интерфейс  <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс.  Получает представление текста <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> объект путем запроса  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> объект, который передается в  <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> метод.  Должен иметь одно <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> объект для каждого представления.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Перехватывает эти пользовательские типы команд в поле кода.  Выход из элемента управления <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> реализация, чтобы обеспечить пользовательские данные завершения и просмотр изменений<br /><br /> Передавать свое <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>объект к представлению текста, вызов  <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .|  
  
## См. также  
 [Разработка службы языка](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Контрольный список: Создание языковую службу для прежних версий](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)