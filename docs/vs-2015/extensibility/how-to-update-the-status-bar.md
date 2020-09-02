---
title: Как обновить строку состояния | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d48b07dd5e4fc1fe745e3669041884c1b8eacd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703145"
---
# <a name="how-to-update-the-status-bar"></a>Практическое руководство. Обновления строки состояния
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Строка состояния** — это панель элементов управления, расположенная в нижней части многих окон приложений, содержащих одну или несколько строк или индикаторов состояния.  
  
### <a name="to-update-the-status-bar"></a>Обновление строки состояния  
  
1. Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> для каждого отдельного объекта представления (DocView), предоставляемого редактором, например представления формы и представления кода.  
  
2. При вызове интегрированной среды разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Обновите информацию в **строке состояния** , вызвав методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> .  
  
    > [!NOTE]
    > Интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> только при первоначальной активации окна документа. В оставшейся части времени, когда окно документа активно, необходимо обновить сведения в **строке состояния** при изменении состояния редактора.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 **Строка состояния** содержит четыре отдельных поля:  
  
- Текст состояния  
  
- Индикатор выполнения  
  
- Анимированный значок  
  
- Сведения о редакторе  
  
  Дополнительные сведения см. в разделе [строки состояния](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e).  
  
  Интегрированная среда разработки автоматически вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> реализации при активации окна документа.  
  
  Средство реализации VSPackage отвечает за обновление текста состояния в строке состояния. Интегрированная среда разработки сбрасывает эту строку в состояние "готов", если текстовое поле состояния имеет значение "пустой текст" ("") во время простоя.  
  
## <a name="see-also"></a>См. также:  
 [Строки состояния](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)
