---
title: Доступ к theText представления с помощью API прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bce39d8ae736d9f7dcda8b18198053f90933b811
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62892165"
---
# <a name="access-the-text-view-by-using-the-legacy-api"></a>Доступ к представлению текста с помощью предыдущих версий API
Представления текста является текст, который хранится в текстовом буфере. Можно получить доступ к представление текста, используя старый API, как показано в следующем разделе.

## <a name="text-view-object"></a>Объект представления текста
 Каждое представление связан с его собственной текстового буфера, а представления — это окно на данные в буфере. На следующей схеме показаны основные интерфейсы объект представления текста, который представляется <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.

 ![Объект представления текста Visual Studio](../extensibility/media/vstextview.gif)

 Это представление является способа представления текста в буфере. Он включает функции, такие как перенос по словам, а также режим структуры, отображаемые в представлении не точное представление текста в буфере.

 Представление позволяет другим службам или процессы, чтобы перехватывать входящие команды и работать с ними, прежде чем представление работает с ними. Наиболее распространенные службы, чтобы сделать это — это служба языка. Языковая служба может потребоваться, например, перехватывать команду клавишу ВВОД, чтобы пользовательские отступов поведение или средство ряд советов.

## <a name="add-functionality-to-the-text-view"></a>Добавление функциональности к текстовому представлению
 Можно настроить поведение текстового представления путем обработки определенных нажатий клавиш. Для перехвата нажатия клавиш, реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> в объекте и укажите целевой объект команды (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) к командам монитора и отсекаемого отрезка.

 Представление текста используется последовательный архитектура для фильтров команд. Новые фильтры команды (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объекты) добавляются в последовательность путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод.

 Уведомление о событии для представления текста осуществляется с помощью предложения <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents> интерфейс. Реализация этого интерфейса в объекте клиента для получения уведомлений об изменениях представления текста. Предоставлять этот интерфейс для представления текста с помощью <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> интерфейс для представления текста для получения уведомления об изменениях из представления.

## <a name="see-also"></a>См. также

- [Изменение параметров представления с помощью предыдущих версий API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)
- [Использование диспетчера текстов для наблюдения за глобальные параметры](../extensibility/using-the-text-manager-to-monitor-global-settings.md)