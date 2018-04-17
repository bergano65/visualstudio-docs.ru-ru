---
title: С помощью диспетчера текстов для наблюдения за глобальные параметры | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e6c61a6859a2e8d359b2185ce959aa941944380f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>С помощью диспетчера текстов для наблюдения за глобальные параметры
При реализации базового редактора необходимо отслеживать изменения, сделанные глобальные параметры, так как эти изменения могут повлиять на ваш экземпляр редактора. Можно отслеживать изменения путем прослушивания события, вызванные диспетчера текстов. Например при указании глобального предпочтение внешний вид или поведение компонента в редакторе ядра, например его объект данных документа, диспетчер текста сохраняет эти данные и передает их все затронутые клиенты.  
  
## <a name="text-manager-functions"></a>Диспетчер текста функции  
 Диспетчер текста вызывает события для некоторых параметров, включая следующие:  
  
-   Является ли буфер — в системе управления версиями  
  
-   Как зарегистрироваться для уведомления об изменении файла  
  
-   Как для отслеживания представлений, к которым связаны с определенным буферов  
  
-   Выделение цветом установок текста  
  
-   Вкладки и места установки  
  
 Диспетчер текста не управляются настроек, которые уникальны для данного языка. Эти параметры должны управляться каждая языковая служба.  
  
 Уведомление о событии для диспетчера текстов обеспечивается <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> интерфейса. Реализация этого интерфейса на клиентском компьютере для обработки событий вызвал диспетчера текстов. Регистрация для этих событий с помощью <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> интерфейс диспетчера текстов.  
  
## <a name="see-also"></a>См. также  
 [В редакторе Core](../extensibility/inside-the-core-editor.md)   
 [Возможности редактора](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)