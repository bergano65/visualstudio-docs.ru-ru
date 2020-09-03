---
title: Размещение IntelliSense | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c378aec6822a436de0d8fc2656fcac7be4149f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203895"
---
# <a name="intellisense-hosting"></a>Размещение IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio обеспечивает размещение IntelliSense. Размещение функция intellsense отображает позволяет предоставить IntelliSense для кода, который не размещается в текстовом редакторе Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Использование технологии размещения IntelliSense  
 В Visual Studio любой код, имеющий доступ к набору завершения и текстовому буферу, может получать окна IntelliSense из любого места в пользовательском интерфейсе. Некоторые примеры сценариев этого находятся в окне **Контрольные значения** или в поле Условие окна Свойства точки останова.  
  
### <a name="implementation-interfaces"></a>Интерфейсы реализации  
  
#### <a name="ivsintellisensehost"></a>ивсинтеллисенсехост  
 Любой компонент пользовательского интерфейса, размещающий всплывающие окна IntelliSense, должен поддерживать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейс. Текстовое представление основного редактора по умолчанию включает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> реализацию стандартного интерфейса для хранения текущих функций IntelliSense. В большинстве случаев методы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейса представляют собой подмножество того, что реализовано в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейсе. Подмножество включает обработку пользовательского интерфейса IntelliSense, управление курсором и выделение, а также простую функцию замены текста. Кроме того, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейс поддерживает отдельные IntelliSense "subject" и "Context", чтобы можно было предоставить функцию IntelliSense для субъектов, которые не существуют непосредственно в текстовом буфере, используемом для контекста.  
  
#### <a name="ivsintellisensehostgethostflags"></a>Ивсинтеллисенсехост. Жесостфлагс  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>Поставщик интерфейса должен реализовать метод, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> чтобы позволить клиенту определить, какой тип функций IntelliSense поддерживает узел.  
  
 Флаги узла, определенные в [интеллисенсехостфлагс](../extensibility/intellisensehostflags.md), приведены ниже.  
  
|Флаг узла IntelliSense|Описание|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Установка этого флага означает, что буфер контекста доступен только для чтения, а редактирование выполняется только внутри текста темы.|  
|IHF_NOSEPERATESUBJECT|Установка этого флага означает, что отдельная тема IntelliSense отсутствует. Субъект существует в буфере контекста, например в традиционной <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> системе IntelliSense.|  
|IHF_SINGLELINESUBJECT|Установка этого флага означает, что субъект не поддерживает многострочный режим, например, в одной строке редактирования в окне **Контрольные значения** .|  
|IHF_FORCECOMMITTOCONTEXT|Если этот флаг установлен и буфер контекста необходимо обновить, узел включит в буфере контекста флаг "только для чтения", который будет пропущен, и изменения для продолжения.|  
|IHF_OVERTYPE|Редактирование (в теме или контексте) должно выполняться в режиме переввода.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>Ивсинтеллисенсехост. Бефорекомплеторкоммит и Ивсинтеллисенсехост. Афтеркомплеторкоммит  
 Эти методы обратного вызова вызываются окном завершения до и после фиксации текста для включения предварительной обработки и последующей обработки.  
  
#### <a name="ivsintellisensecompletor"></a>ивсинтеллисенсекомплетор  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor>Интерфейс — это версия стандартного окна завершения, которая используется в интегрированной среде разработки (IDE). Любой <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> интерфейс может быстро реализовать IntelliSense с помощью этого интерфейса комплетор.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
