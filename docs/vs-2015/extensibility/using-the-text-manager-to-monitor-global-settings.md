---
title: Использование диспетчера текста для мониторинга глобальных параметров | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ece51450b8344ae4715a912399ec538171a26a5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695466"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Использование диспетчера текстов для мониторинга глобальных параметров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При реализации базового редактора необходимо отслеживать изменения, внесенные в глобальные параметры, так как эти изменения могут повлиять на ваш экземпляр редактора. Можно отвести отслеживание изменений, прослушивая события, вызываемые диспетчером текста. Например, при указании глобального предпочтения для внешнего вида или поведения компонента в основном редакторе, например объекта данных документа, текстовый диспетчер сохраняет эти сведения и передает их всем затронутым клиентам.  
  
## <a name="text-manager-functions"></a>Функции диспетчера текста  
 Диспетчер текста создает события для ряда параметров, включая следующие:  
  
- Находится ли буфер в системе управления исходным кодом  
  
- Как зарегистрироваться для получения уведомлений об изменении файлов  
  
- Как контролировать, какие представления связаны с определенными буферами  
  
- Настройки цветовой палитры текста  
  
- Параметры табуляции и пробелов  
  
  Параметры, уникальные для данного языка, не управляются диспетчером текста. Эти параметры должны управляться каждой языковой службой.  
  
  Уведомление о событии для диспетчера текстов предоставляется <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> интерфейсом. Реализуйте этот интерфейс для клиентского объекта, чтобы обрабатывались события, вызванные диспетчером текста. Для регистрации этих событий используется <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> интерфейс в диспетчере текстов.  
  
## <a name="see-also"></a>См. также:  
 [Внутри основного редактора](../extensibility/inside-the-core-editor.md)   
 [Функции редактора](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
