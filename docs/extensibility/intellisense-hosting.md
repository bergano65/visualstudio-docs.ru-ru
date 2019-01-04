---
title: Размещение IntelliSense | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ba74b54e074a7522783e63c367586a943607857
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838181"
---
# <a name="intellisense-hosting"></a>Размещение IntelliSense
Visual Studio позволяет обеспечить работу IntelliSense. Intellsense отображает размещение позволяет предоставить IntelliSense для кода, который не будет размещено в текстовом редакторе Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Использование размещения IntelliSense  
 В Visual Studio любой код, который имеет доступ к набора завершений и текстовый буфер можно получить IntelliSense windows из любого места в пользовательском интерфейсе (UI). Примеры сценариев по это, завершение в **Watch** окно или в поле "условие" окна свойств точки останова.  
  
### <a name="implementation-interfaces"></a>Реализация интерфейсов  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Любой компонент пользовательского интерфейса, на котором размещена IntelliSense всплывающие окна должен поддерживать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейс. Представление текстового редактора core по умолчанию включает в себя акций <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> реализацию для сохранения текущего IntelliSense функциональности интерфейса. В большинстве случаев методы класса <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейса представляют собой подмножество что реализуется на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейс. Подмножество включает обработку пользовательского интерфейса IntelliSense, курсор и выбора манипуляции и функции замены простого текста. Кроме того <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейс включает отдельный IntelliSense «тема» и «контекст» чтобы IntelliSense можно предоставить для субъектов, которые не существуют непосредственно в текстовом буфере, который используется для контекста.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Должен реализовывать интерфейс поставщика <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> поддерживает метод, чтобы клиент мог определить, какой тип IntelliSense функции узла.  
  
 Флаги узла, определенный в [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), приведены ниже.  
  
|Флаг узла IntelliSense|Описание|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Этот флаг означает, что контекстный буфер доступен только для чтения и редактирования выполняется только в пределах текст темы.|  
|IHF_NOSEPERATESUBJECT|Это означает, что флаг, существует задается без отдельной темы IntelliSense. Субъект существует в буфере контекста, такие как в традиционных <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> система IntelliSense.|  
|IHF_SINGLELINESUBJECT|Этот флаг означает, что субъект не может, например, при редактировании одной строки в многострочном **Watch** окна.|  
|IHF_FORCECOMMITTOCONTEXT|Если этот флаг установлен, ее необходимо обновить буфер контекста, узел включает флаг буфер контекста пропускаются только для чтения и изменения, чтобы продолжить.|  
|IHF_OVERTYPE|Изменения (в предмета или контекста) должны выполняться в режиме замены.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit и IVsIntellisenseHost.AfterCompletorCommit  
 Эти методы обратного вызова, называются в окне завершения до и после текста фиксируется, чтобы включить предварительной обработки и постобработки.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> Интерфейс является воссоздаваемым версии standard завершения окна, которое используется в интегрированной среде разработки (IDE). Любой <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейс быстро можно реализовать с помощью этого интерфейса объект completor IntelliSense.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop>