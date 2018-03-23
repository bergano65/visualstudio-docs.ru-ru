---
title: Доступ к theText представления с помощью API прежних версий | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7aa879847e87b1a0372e2a8e9a3a6ec712041a56
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Доступ к theText представления с помощью API прежних версий
Текстовое представление — представления текста, который хранится в буфер текста. Текстовое представление доступны с помощью предыдущих версий API, как показано в следующем разделе.

## <a name="text-view-object"></a>Объект представления текста
 Каждое представление связан с буфера текста, а представление — это окно на основе данных в буфере. На следующей диаграмме показаны ключевые интерфейсы объект представления текста, который представляется <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.

 ![Объект представления текста Visual Studio](../extensibility/media/vstextview.gif "vstextview") объект представления текста

 Представление — это способ представления текста в буфере. Он включает функции, например перенос по словам и структурирование, чтобы появиться в представлении не точное представление текста в буфере.

 Представление включает других служб или процессов, чтобы перехватывать входящие команды и работать с ними, прежде чем представление работает с ними. Наиболее распространенной службой для этого является служба языка. Языковая служба может потребоваться, например, перехвата команды клавишу ВВОД для предоставления пользовательских отступов советы поведение или средства.

## <a name="adding-functionality-to-the-text-view"></a>Добавление функциональных возможностей в представление текста
 Можно настроить поведение представления текста с помощью обработки определенного нажатия клавиш. Для перехвата нажатия клавиш, необходимо реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> объекта и укажите конечный объект команды (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) для монитора и отсекаемый отрезок команд.

 Текстовое представление последовательного архитектурой фильтры команд. Новые фильтры команды (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объектов) добавляются в последовательность путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод.

 Уведомление о событии для представления текста предоставляется с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents> интерфейса. Реализация этого интерфейса на объект клиента будет получать уведомления об изменениях для представления текста. Предоставить этот интерфейс для представления текста с помощью <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> интерфейс для представления текста, чтобы получать уведомления об изменениях из представления.

## <a name="see-also"></a>См. также

- [Изменение параметров представления с помощью API прежних версий](../extensibility/changing-view-settings-by-using-the-legacy-api.md)
- [С помощью диспетчера текстов для наблюдения за глобальные параметры](../extensibility/using-the-text-manager-to-monitor-global-settings.md)