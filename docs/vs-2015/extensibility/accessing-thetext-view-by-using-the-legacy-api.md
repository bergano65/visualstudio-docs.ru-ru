---
title: Доступ к theText представления с помощью API прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f9396e4523e38e7313efb5668c4680f551558ab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978893"
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Доступ к theText представления с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Представления текста является текст, который хранится в текстовом буфере. Можно получить доступ к представление текста, используя старый API, как показано в следующем разделе.  
  
## <a name="text-view-object"></a>Объект представления текста  
 Каждое представление связан с его собственной текстового буфера, а представления — это окно на данные в буфере. На следующей схеме показаны основные интерфейсы объект представления текста, который представляется <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.  
  
 ![Объект представления текста Visual Studio](../extensibility/media/vstextview.gif "vstextview")  
Объект представления текста  
  
 Это представление является способа представления текста в буфере. Он включает функции, такие как перенос по словам, а также режим структуры, отображаемые в представлении не точное представление текста в буфере.  
  
 Представление позволяет другим службам или процессы, чтобы перехватывать входящие команды и работать с ними, прежде чем представление работает с ними. Наиболее распространенные службы, чтобы сделать это — это служба языка. Языковая служба может потребоваться, например, перехватывать команду клавишу ВВОД, чтобы пользовательские отступов поведение или средство ряд советов.  
  
## <a name="adding-functionality-to-the-text-view"></a>Добавление функции для текстового представления.  
 Можно настроить поведение текстового представления путем обработки определенных нажатий клавиш. Для перехвата нажатия клавиш, реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> в объекте и укажите целевой объект команды (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) к командам монитора и отсекаемого отрезка.  
  
 Представление текста используется последовательный архитектура для фильтров команд. Новые фильтры команды (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объекты) добавляются в последовательность путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод.  
  
 Уведомление о событии для представления текста осуществляется с помощью предложения `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` интерфейс. Реализация этого интерфейса в объекте клиента для получения уведомлений об изменениях представления текста. Предоставлять этот интерфейс для представления текста с помощью <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> интерфейс для представления текста для получения уведомления об изменениях из представления.  
  
## <a name="see-also"></a>См. также  
 [Изменение параметров представления с помощью API прежних версий](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Использование диспетчера текстов для мониторинга глобальных параметров](../extensibility/using-the-text-manager-to-monitor-global-settings.md)
