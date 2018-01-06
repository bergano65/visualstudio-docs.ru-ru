---
title: "Как: обеспечения автоматизации Windows | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 17cf60573b6feb9fd317116eec4639dbf88f6089
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-automation-for-windows"></a>Как: обеспечения автоматизации Windows
Чтобы обеспечить автоматизацию для окна документов и средств. Предоставление автоматизации рекомендуется всякий раз, когда требуется освободить объекты автоматизации на окно и среде не предоставить объект готовых автоматизации, как в список задач.  
  
## <a name="automation-for-tool-windows"></a>Автоматизация для окон инструментов  
 Среда предлагает автоматизации на окно инструментов, возвращая стандартного <xref:EnvDTE.Window> объекта, как описано в следующей процедуре:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Для обеспечения автоматизации окна инструментов  
  
1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод через среду с <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> как `VSFPROPID` для получения `Window` объекта.  
  
2.  Если вызывающий объект запрашивает объект автоматизации конкретного VSPackage для вашего окна инструментов через <xref:EnvDTE.Window.Object%2A>, среда вызывает метод `QueryInterface` для `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, или `IDispatch` интерфейсов. Оба `IExtensibleObject` и `IVsExtensibleObject` предоставляют <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> метод.  
  
3.  Если затем вызывает среды `GetAutomationObject` метод передачи `NULL`, ответ, передавая обратно вашего VSPackage-объект.  
  
4.  Если вызов `QueryInterface` для `IExtensibleObject` и `IVsExtensibleObject` завершается ошибкой, то среда вызывает `QueryInterface` для `IDispatch`.  
  
## <a name="automation-for-document-windows"></a>Модель автоматизации для окна документов  
 Стандартный <xref:EnvDTE.Document> объект можно получить из среды, несмотря на то, что редактор может иметь собственную реализацию `T:EnvDTE.Document` объекта путем реализации `IExtensibleObject` интерфейс и реагирование на `GetAutomationObject`.  
  
 Кроме того, редактор предоставляет зависящие от пакета VSPackage объект автоматизации, извлекаемые с помощью <xref:EnvDTE.Document.Object%2A> метод путем реализации `IVsExtensibleObject` или `IExtensibleObject` интерфейсов. [Примеры VSSDK](http://aka.ms/vs2015sdksamples) участвует объекта автоматизации документа RTF.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>