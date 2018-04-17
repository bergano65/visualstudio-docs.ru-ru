---
title: Размещение IntelliSense | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b101460b3867c89862068d99412cd06edb884ef7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="intellisense-hosting"></a>Размещение IntelliSense
Visual Studio позволяет обеспечить работу IntelliSense. IntellSense размещение позволяет предоставить IntelliSense для кода, которая не размещена в текстовом редакторе Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Использование размещения IntelliSense  
 В Visual Studio, любой код, который имеет доступ к набора завершения и буфер текста можно получить IntelliSense windows из любого места в пользовательском интерфейсе (UI). Примеры сценариев данного объекта, завершение в **Контрольные значения** окно или в поле условие окна свойств точки останова.  
  
### <a name="implementation-interfaces"></a>Реализация интерфейсов  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Любой компонент пользовательского интерфейса, на котором размещена IntelliSense всплывающие окна должен поддерживать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейса. Редактор текста по умолчанию основное представление включает stock <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейс реализацию для сохранения текущего функциональные возможности технологии IntelliSense. В большинстве случаев методы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейс представляют собой подмножество о том, что реализуется на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейса. Подмножество включает обработку, курсор и манипуляции выбора и простой текст замены функции IntelliSense пользовательского интерфейса. Кроме того <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейс позволяет отдельные IntelliSense «тема» и «контекст», чтобы IntelliSense, которые могут быть предоставлены для субъектов, которые не существуют непосредственно в буфере, который используется для контекста.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Должен реализовывать интерфейс поставщика <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> поддерживает методы, позволяющие клиенту определить, какой тип IntelliSense возможностей узла.  
  
 Флаги узла, определенного в [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), описаны ниже.  
  
|Флаг узла IntelliSense|Описание|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Этот флаг означает, что буфер контекста параметр только для чтения и редактирования выполняется только в текст темы.|  
|IHF_NOSEPERATESUBJECT|Включение флаг означает, что существует является тема не отдельный IntelliSense. Субъект существует в буфере контекста, например в традиционные <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> система IntelliSense.|  
|IHF_SINGLELINESUBJECT|Этот флаг означает, что субъект не имеет параметра несколько строк может, например, в одной строке изменения в **Контрольные значения** окна.|  
|IHF_FORCECOMMITTOCONTEXT|Если этот флаг установлен, и должны быть обновлены буфер контекста, узел включает флаг буфер контекста, пропускаются только для чтения и изменения, чтобы продолжить.|  
|IHF_OVERTYPE|Изменение (в теме или контекста) должны выполняться в режиме замены.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit и IVsIntellisenseHost.AfterCompletorCommit  
 До и после фиксации, чтобы включить предварительной обработки и последующей обработки текста, то окно завершения вызываются методы обратного вызова.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> Интерфейс является воссоздаваемым версии окна стандартных завершения, используемый интегрированной среды разработки (IDE). Любой <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейс быстро можно реализовать с помощью этого интерфейса completor IntelliSense.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop>