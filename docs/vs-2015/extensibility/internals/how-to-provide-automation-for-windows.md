---
title: Руководство. предоставление автоматизации для Windows | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ea7b79df4e7f3748ec2bc7f5e57c6ecb7dfca5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191843"
---
# <a name="how-to-provide-automation-for-windows"></a>Практическое руководство. Автоматизация для окон
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Вы можете предоставить автоматизацию для окон документов и инструментов. Предоставление автоматизации рекомендуется, если нужно сделать объекты автоматизации доступными в окне, а среда еще не предоставляет готовый объект автоматизации, как это делается в списке задач.  
  
## <a name="automation-for-tool-windows"></a>Автоматизация для окон инструментов  
 Среда предоставляет автоматизацию для окна инструментов, возвращая Стандартный <xref:EnvDTE.Window> объект, как описано в следующей процедуре:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Предоставление автоматизации для окон инструментов  
  
1. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод через среду с <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> `VSFPROPID` параметром AS, чтобы получить `Window` объект.  
  
2. Когда вызывающий объект запрашивает в своем окне инструментария определяемый пакет VSPackage, <xref:EnvDTE.Window.Object%2A> среда вызывает `QueryInterface` для `IExtensibleObject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> `IDispatch` интерфейсов, или. `IExtensibleObject`И `IVsExtensibleObject` предоставляют <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> метод.  
  
3. После того, как среда вызывает `GetAutomationObject` передачу метода `NULL` , ответьте на него, передав объект, относящийся к VSPackage.  
  
4. Если вызывает `QueryInterface` метод `IExtensibleObject` и `IVsExtensibleObject` завершается ошибкой, среда вызывает метод `QueryInterface` для `IDispatch` .  
  
## <a name="automation-for-document-windows"></a>Автоматизация для окон документов  
 Стандартный <xref:EnvDTE.Document> объект также доступен из среды, хотя редактор может иметь собственную реализацию `T:EnvDTE.Document` объекта путем реализации `IExtensibleObject` интерфейса и реагирования на `GetAutomationObject` .  
  
 Кроме того, редактор может предоставить специфический для VSPackage объект автоматизации, полученный с помощью <xref:EnvDTE.Document.Object%2A> метода, путем реализации `IVsExtensibleObject` `IExtensibleObject` интерфейсов или. [Примеры VSSDK](../../misc/vssdk-samples.md) вносят объект автоматизации, относящийся к документу RTF.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
