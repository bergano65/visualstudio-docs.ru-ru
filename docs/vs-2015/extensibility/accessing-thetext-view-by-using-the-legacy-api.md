---
title: Доступ к представлению Сетекст с помощью API прежних версий | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184962"
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Доступ к текстовому представлению с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Текстовое представление — это представление текста, хранящегося в текстовом буфере. Доступ к представлению текста можно получить с помощью API прежних версий, как показано в следующем разделе.  
  
## <a name="text-view-object"></a>Объект представления текста  
 Каждое представление связано с собственным текстовым буфером, а представление — с окном данных в буфере. На следующей диаграмме показаны основные интерфейсы объекта представления текста, представленного <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 ![Объект представления текста Visual Studio](../extensibility/media/vstextview.gif "встекствиев")  
Объект представления текста  
  
 Представление — это способ представления текста в буфере. Он включает такие функции, как перенос по словам и структурирование, так что отображаемые в представлении элементы не являются точным представлением текста в буфере.  
  
 Представление позволяет другим службам или процессам перехватывать входящие команды и реагировать на них до того, как в них будет действовать представление. Наиболее распространенной службой для этого является языковая служба. Языковая служба может потребовать, например, перехватить команду для клавиши ВВОД, чтобы обеспечить пользовательское поведение отступа или подсказки.  
  
## <a name="adding-functionality-to-the-text-view"></a>Добавление функциональных возможностей в текстовое представление  
 Поведение представления текста можно настроить, обрабатывая определенные нажатия клавиш. Чтобы перехватить нажатия клавиш, необходимо реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> объект на объекте и предоставить целевой объект команды ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ) для мониторинга и перехвата команд.  
  
 Текстовое представление использует последовательную архитектуру для фильтров команд. Новые фильтры команд ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объекты) добавляются в последовательность путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метода.  
  
 Уведомление о событии для текстового представления предоставляется с помощью `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` интерфейса. Реализуйте этот интерфейс для клиентского объекта, чтобы получить уведомления об изменениях в текстовом представлении. Предоставьте этот интерфейс для текстового представления, используя <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> интерфейс в представлении текста для получения уведомлений об изменениях в представлении.  
  
## <a name="see-also"></a>См. также:  
 [Изменение параметров представления с помощью API прежних версий](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Использование диспетчера текстов для мониторинга глобальных параметров](../extensibility/using-the-text-manager-to-monitor-global-settings.md)
