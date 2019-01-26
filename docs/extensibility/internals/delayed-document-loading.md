---
title: Отложенная загрузка документов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 973ea13ca7f175515e0e730cacdf7b1bdd75355b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922981"
---
# <a name="delayed-document-loading"></a>Отложенная загрузка документов
При повторном открытии решения Visual Studio, большая часть указанных документах не загружаются. Рамка окна документа создается в состоянии ожидания инициализации, а заполнитель документ (кадр заглушки) помещается в таблице под управлением документов (RDT).  
  
Расширение может вызвать без необходимости загрузки путем запроса элементов в документах, прежде чем они загружаются, документы проекта, которые можно увеличить общий объем памяти для Visual Studio.  
  
## <a name="document-loading"></a>Загрузка документов  
Фрейм заглушки и выполнения полной инициализации когда пользователь получает доступ к документа, например, выбрав вкладку окна области. Документ также может быть инициализирован с расширением, которое запрашивает данные документа, либо доступ к RDT непосредственно получить данные документа или при доступе к RDT косвенно, сделав один из следующих вызовов:  
  
- Рамка окна <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> метод.  
  
- Рамка окна <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод на любом из следующих свойств:  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
- Если расширение использует управляемый код, не следует вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> Если вы не уверены, что документ не находится в состоянии ожидания инициализации, или полной инициализации документа. Потому, что этот метод всегда возвращает документ объект данных, чтобы создать его при необходимости. Вместо этого следует вызвать один из методов на `IVsRunningDocumentTable4` интерфейс.  
  
- Если расширение использует C++, вы можете передать `null` для параметров, не нужно.  
  
- Можно избежать ненужных документа, загрузка путем вызова одного из следующих методов, прежде чем запрашивать соответствующие свойства, прежде чем запрашивать другие свойства:  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Этот метод возвращает <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> объект, который включает значение <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Если документ не был инициализирован.  
  
Чтобы узнать при загрузке документа, подписавшись на событие RDT, которое возникает, когда документ будет полностью инициализирован. Существуют две возможности:  
  
- Если приемник событий реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, вы можете подписаться на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
- В противном случае вы можете подписаться на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  

 Следующий пример — сценарий доступа гипотетической документа: Visual Studio, хочет расширения содержал некую информацию об открытых документов, для экземпляра редактирования заблокировать count и что-нибудь о данные документа. Он перечисляет документы в RDT с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, затем вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> для каждого документа, для извлечения данных с count и документа блокировку редактирования. Если документ находится в состоянии ожидания инициализации, запрашивающего данные документа приводит к инициализироваться без необходимости.  
  
 Более эффективный способ доступа к документа является использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> для получения количества блокировку редактирования, а затем используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> для определения, был ли инициализирован документа. Если флаги не включают <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, документ уже был инициализирован и запрос данных документа с <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> не вызывает инициализацию ненужные. Если включить флаги <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, модуль следует избегать, запрашивающего данные документа, пока не будет инициализирован документа. Эта инициализация могут быть обнаружены в `OnAfterAttributeChange(Ex)` обработчик событий.  
  
## <a name="test-extensions-to-see-if-they-force-initialization"></a>Проверка расширений, чтобы увидеть, если они принудительно инициализации  
 Нет не обозначена указать документ был ли инициализирован, чтобы он может быть трудно узнать, если расширение после инициализации. Можно задать раздел реестра, который упрощает проверку подлинности, так как вызывает Заголовок каждого документа, который не был инициализирован полностью текста *[заглушка]* в заголовке.  
  
 В **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad**, задайте **StubTabTitleFormatString** для  *{0} [заглушка]*.