---
title: "Отложенная загрузка документов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 794eccaf59b65044840d459bbde2e17eab8684a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="delayed-document-loading"></a>Отложенная загрузка документов
При повторном открытии решения Visual Studio, большинство связанные документы не загружаются. Рамка окна документа создается в состоянии ожидания инициализации, а заполнитель документа (называемые фрейм заглушки) помещается в таблице под управлением документа (RDT).  
  
 Расширение может привести к документы проекта без необходимости загружать с помощью запроса элементов в документах, прежде чем они будут загружены. Это может увеличить общий объем памяти для Visual Studio.  
  
## <a name="document-loading"></a>Загрузка документов  
 Фрейм заглушки и выполнения полностью инициализирован, когда пользователь получает доступ к документу, например при выборе вкладки окна. Документ также могут инициализироваться с помощью расширения, который запрашивает данные документа путем доступа к RDT непосредственно для получения данных документа или доступ к RDT косвенно с одного из следующих вызовов:  
  
-   Метод show фрейм окна: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
-   Рамка окна GetProperty — метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> на любой из следующих свойств:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 Если модуль использует управляемый код, не следует вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> только что документ не находится в состоянии ожидания инициализации или полной инициализации документа... Это, поскольку этот метод всегда возвращает документов объект данных, создавая его при необходимости. Вместо этого следует вызывать один из методов в интерфейсе IVsRunningDocumentTable4.  
  
 Если модуль использует C++, вы можете передать `null` для параметров, которые необходимо исключить.  
  
 Загрузка ненужные документа можно избежать путем вызова одного из следующих методов, прежде чем запрашивать соответствующие свойства: диаграммами других свойств.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Этот метод возвращает <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> объект, который содержит значение для <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Если документ не был инициализирован.  
  
 Можно узнать при загрузке документа подписавшись на RDT событие, которое возникает, когда документ будет полностью инициализирован. Есть две возможности:  
  
-   Если приемник событий реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, можно подписаться на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
-   В противном случае вы можете подписаться на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
 Следующие встречается гипотетической документа доступа. Visual Studio расширения должны отображаться некоторые сведения об открытых документов, для экземпляра редактирования заблокировать count и какое-либо данных документа. Он перечисляет документы с помощью RDT <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, затем вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> для каждого документа для получения данных документ и счетчик блокировки изменения. Если документ находится в состоянии ожидания инициализации, запрашивающего данные документа приводит к инициализироваться без необходимости.  
  
 Более эффективный способ сделать это является использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> для подсчета блокировки изменения, а затем использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> для определения, был ли инициализирован документа. Если флаги не включают <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, документ уже инициализирован и запрос данных документа с <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> не вызывает все ненужные инициализации. Если включить флаги <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, следует избегать расширения, запрашивающего данные документа до инициализации документа. Это могут быть обнаружены в обработчике событий OnAfterAttributeChange(Ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Тестирование расширений для просмотра, если они принудительно инициализации  
 Нет не наглядно обозначена для указания документ был ли инициализирован, поэтому он может быть трудно определить, если расширение после инициализации. Можно задать раздел реестра, который упрощает проверку, так как вызывает Заголовок каждого документа, который не был инициализирован полностью чтобы текст `[Stub]` в заголовке.  
  
 В **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]**, задайте **StubTabTitleFormatString** для **{0} [заглушка]**.