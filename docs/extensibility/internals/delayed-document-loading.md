---
title: "Отложенная загрузка документов | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Отложенная загрузка документов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

При повторном открытии решения Visual Studio, большая часть связанные документы не загружаются. Фрейм окна документа создается в состоянии ожидания инициализации, а заполнитель документ \(фрейм заглушки\) помещается в таблице под управлением документа \(RDT\).  
  
 Расширение может привести к документы проекта без необходимости загрузки с помощью запроса элементов в документах, прежде чем они будут загружены. Это может увеличить общий объем памяти для Visual Studio.  
  
## Загрузка документов  
 Фрейм заглушки и документ полностью инициализируется при доступе пользователя к документа, например при выборе вкладки окна. Документ также может быть инициализирован с расширением, которое запрашивает данные документа путем доступа к RDT непосредственно получить данные документа или косвенного доступа к RDT, сделав один из следующих вызовов:  
  
-   Метод show окна: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
-   Метод GetProperty окна <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> на любой из следующих свойств:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 Если расширение использует управляемый код, не следует вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> Если вы не уверены, что документ не находится в состоянии ожидания инициализации или полной инициализации документа... Это, поскольку этот метод всегда возвращает документ объект данных, создавая его при необходимости. Вместо этого следует вызвать один из методов для интерфейса IVsRunningDocumentTable4.  
  
 Если расширение использует C\+\+, вы можете передать `null` параметров не требуется.  
  
 Загрузка ненужные документа можно избежать путем вызова одного из следующих методов, прежде чем запрашивать соответствующие свойства: Прежде чем запрашивать другие свойства.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Этот метод возвращает <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> объекта, который содержит значение <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Если документ не был инициализирован.  
  
 Чтобы узнать при загрузке документа можно подписаться на событие RDT, которое возникает, когда документ полностью инициализирован. Есть две возможности:  
  
-   Если приемник событий реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, вы можете подписаться на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
-   В противном случае, вы можете подписаться на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
 Ниже приведен сценарий доступа гипотетической документов. Visual Studio расширения должны отображаться некоторые сведения об открытых документов, для экземпляра редактирования count и блокировать некоторые данные документа. Перечисляет документы в RDT с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, затем вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> для каждого документа, для получения данных счетчика и документа изменить блокировки. Если документ находится в состоянии ожидания инициализации, запрашивающих данные документа приводит к инициализироваться без необходимости.  
  
 Более эффективный способ сделать это является использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> для подсчета блокировку изменения, а затем использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> для определения, был ли инициализирован документа. Если флаги не содержат <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, документ уже инициализирован и запрашивает данные документа с <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> не вызывает все ненужные инициализации. Если включить флаги <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, следует избегать расширения, запрашивающего данные документа, пока не будет инициализирован документа. Это могут быть обнаружены в обработчике событий OnAfterAttributeChange\(Ex\).  
  
## Тестирование расширений для просмотра, если они принудительно инициализации  
 Нет, не видны подсказки для указания документ был ли инициализирован, поэтому он может быть трудно найти Если расширение вынуждает инициализацию. Можно задать раздел реестра, который упрощает проверку, так как вызывает Заголовок каждого документа, который не был инициализирован полностью чтобы текст `[Stub]` в заголовке.  
  
 В **HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\BackgroundSolutionLoad\]**, задайте **StubTabTitleFormatString** для **{0} \[заглушка\]**.