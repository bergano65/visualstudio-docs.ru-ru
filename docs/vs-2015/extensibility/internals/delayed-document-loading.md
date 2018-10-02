---
title: Отложенная загрузка документов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a3469484518a4d802c8fc0de11a32533fa429d3d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560449"
---
# <a name="delayed-document-loading"></a>Отложенная загрузка документов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [отложенной загрузке документа](https://docs.microsoft.com/visualstudio/extensibility/internals/delayed-document-loading).  
  
При повторном открытии решения Visual Studio, большая часть указанных документах не загружаются. Рамка окна документа создается в состоянии ожидания инициализации, а заполнитель документ (кадр заглушки) помещается в таблице выполняющихся документов (RDT).  
  
 Расширение может привести к документы проекта без необходимости загрузки путем запроса элементов в документах, прежде чем они будут загружены. Это может увеличить общий объем памяти для Visual Studio.  
  
## <a name="document-loading"></a>Загрузка документов  
 Фрейм заглушки и выполнения полной инициализации когда пользователь получает доступ к документа, например, выбрав вкладку окна области. Документ также может быть инициализирован с расширением, которое запрашивает данные документа, либо доступ к RDT непосредственно получить данные документа или при доступе к RDT косвенно, сделав один из следующих вызовов:  
  
-   Метод отображения окна: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
-   Рамка окна метод GetProperty <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> на любом из следующих свойств:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 Если расширение использует управляемый код, не следует вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> Если вы не уверены, что документ не находится в состоянии ожидания инициализации, или полной инициализации документа... Это обусловлено тем, этот метод всегда возвращает документ объект данных, чтобы создать его при необходимости. Вместо этого следует вызывать один из методов в интерфейсе IVsRunningDocumentTable4.  
  
 Если расширение использует C++, вы можете передать `null` для параметров, не нужно.  
  
 Загрузка ненужных документов можно избежать путем вызова одного из следующих методов, прежде чем запрашивать соответствующие свойства: Прежде чем запрашивать другие свойства.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Этот метод возвращает <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> объект, который включает значение <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Если документ не был инициализирован.  
  
 Чтобы узнать при загрузке документа, подписавшись на событие RDT, которое возникает, когда документ будет полностью инициализирован. Существуют две возможности:  
  
-   Если приемник событий реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, вы можете подписаться на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
-   В противном случае вы можете подписаться на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
 Ниже приведен сценарий доступа гипотетической документа. Visual Studio, расширения должны отображаться некоторые сведения об открытых документов, для экземпляра редактирования заблокировать count и что-нибудь о данные документа. Он перечисляет документы в RDT с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, затем вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> для каждого документа, для извлечения данных с count и документа блокировку редактирования. Если документ находится в состоянии ожидания инициализации, запрашивающего данные документа приводит к инициализироваться без необходимости.  
  
 Более эффективный способ сделать это позволяет использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> для получения количества блокировку редактирования, а затем используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> для определения, был ли инициализирован документа. Если флаги не включают <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, документ уже был инициализирован и запрос данных документа с <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> не вызывает инициализацию ненужные. Если включить флаги <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, модуль следует избегать, запрашивающего данные документа, пока не будет инициализирован документа. Это можно обнаружить в обработчике событий OnAfterAttributeChange(Ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Тестирование расширения, чтобы увидеть, если они принудительно инициализации  
 Нет не обозначена указать документ был ли инициализирован, чтобы он может быть трудно узнать, если расширение после инициализации. Можно задать раздел реестра, который упрощает проверку подлинности, так как вызывает Заголовок каждого документа, который не был инициализирован полностью текста `[Stub]` в заголовке.  
  
 В **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]**, задайте **StubTabTitleFormatString** для  **{0} [заглушка]**.

