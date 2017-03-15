---
title: "Размещение IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - размещение IntelliSense"
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Размещение IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio включает размещение IntelliSense.  Размещение IntellSense позволяет обеспечить IntelliSense для кода, не размещенного текстового редактора Visual Studio.  
  
## IntelliSense при размещении потребление  
 В Visual Studio любой код, имеющий доступ к набору завершения и текстовый буфер окна IntelliSense могут получить из любого места внутри пользовательского интерфейса \(ui\).  Некоторые сценарии в примере этого завершение **Контрольное значение** окно или в поле условие окна свойства точки останова.  
  
### Интерфейсы реализации  
  
#### IVsIntellisenseHost  
 Любой компонент пользовательского интерфейса, всплывающие окна IntelliSense основных приложений должны поддерживать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейс.  По умолчанию взаимодействие включает текстовое представление редактора reserve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> реализация интерфейса для сохранения текущую функциональность технологии IntelliSense.  В большинстве случаев методы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейс представляет подмножество, что реализуется на  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейс.  Подмножество включает обработку пользовательского интерфейса IntelliSense, управление курсора и выделения и простую возможность замены текста.  Кроме того, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейс содержит отдельную технологию IntelliSense ,посвященном" и "контекст" для IntelliSense можно защитить, которые не существуют непосредственно в текстовом буфере, который используется для контекста.  
  
#### IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> поставщик интерфейса, должен реализовывать  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> метод, чтобы позволить клиенту указать, какой тип функций IntelliSense, поддерживаемых основным приложением.  
  
 Флаги, указанные внутри основного приложения IntellisenseHostFlags, summarize ниже.  
  
|Пометить узла IntelliSense|Описание|  
|--------------------------------|--------------|  
|IHF\_READONLYCONTEXT|Установка этого пометить означает, что буфер контекста только для чтения и редактирования происходит только в текст темы.|  
|IHF\_NOSEPERATESUBJECT|Установка этого пометить означает, что отдельный раздел IntelliSense.  Раздел существует в буфере контекста, например в прежних версий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> система IntelliSense.|  
|IHF\_SINGLELINESUBJECT|Установка этого пометить означает, что раздел многополосные способные, например в " правка " на одной линии **Контрольное значение** окна.|  
|IHF\_FORCECOMMITTOCONTEXT|Если этот пометить набор и буфер контекста необходимо обновить, то узел включается только для чтения в буфере контекста пометить игнорируемого и правках, чтобы продолжить.|  
|IHF\_OVERTYPE|Редактирование в разделе \(или\), должен быть выполнен в контексте подставляет режим.|  
  
#### IVsIntellisenseHost.BeforeCompletorCommit и IVsIntellisenseHost.AfterCompletorCommit  
 Эти обратные вызовы называется окном завершения фиксации до и после текста, чтобы включить предварительная обработка и постпроцессирование.  
  
#### IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> интерфейс версия co\-creatable стандартного окна завершения, который используется средой разработки \(ide\).  Any <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейс может быстро реализовывать IntelliSense с помощью этого интерфейса completor.  
  
## См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop>