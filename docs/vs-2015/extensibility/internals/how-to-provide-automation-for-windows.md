---
title: 'Практическое: Автоматизация для Windows | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9dd3dee875cfe7af7e482204130abc53bcaba616
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305751"
---
# <a name="how-to-provide-automation-for-windows"></a>Практическое: Автоматизация для Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Вы можете предоставить автоматизация для окон документов и средств. Предоставление автоматизации рекомендуется всякий раз, когда вы хотите сделать объекты автоматизации доступными в окне и среде уже не предоставить объект готовые службы автоматизации, как в случае со списком задач.  
  
## <a name="automation-for-tool-windows"></a>Модель автоматизации для инструментов Windows  
 Среды обеспечивает автоматизацию в окне инструментов, возвращая стандартный <xref:EnvDTE.Window> объекта, как описано в следующей процедуре:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Для обеспечения автоматизации окна инструментов  
  
1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод через среду со <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> как `VSFPROPID` для получения `Window` объекта.  
  
2.  Когда вызывающий объект запрашивает объект автоматизации определенного VSPackage для вашего окна инструментов через <xref:EnvDTE.Window.Object%2A>, среда вызывает метод `QueryInterface` для `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, или `IDispatch` интерфейсов. Оба `IExtensibleObject` и `IVsExtensibleObject` предоставляют <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> метод.  
  
3.  Когда среде затем вызывает метод `GetAutomationObject` метод `NULL`, ответ, передав резервного объекта определенного VSPackage.  
  
4.  Если вызов `QueryInterface` для `IExtensibleObject` и `IVsExtensibleObject` завершается ошибкой, то среда вызывает `QueryInterface` для `IDispatch`.  
  
## <a name="automation-for-document-windows"></a>Модель автоматизации для документа Windows  
 Стандартный <xref:EnvDTE.Document> объекта также доступна из среды, несмотря на то, что редактор может иметь собственную реализацию `T:EnvDTE.Document` объекта путем реализации `IExtensibleObject` интерфейс и реагирование на них `GetAutomationObject`.  
  
 Кроме того, редактор можно предоставить объект автоматизации определенного VSPackage, полученные через <xref:EnvDTE.Document.Object%2A> метод путем реализации `IVsExtensibleObject` или `IExtensibleObject` интерфейсов. [Примеры VSSDK](../../misc/vssdk-samples.md) участвует объект автоматизации конкретного документа RTF.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>

