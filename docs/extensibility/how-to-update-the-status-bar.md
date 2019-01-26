---
title: Как выполнить Обновление строки состояния | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49661e379c81bac935e2d2ae2279e32d548eb698
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929878"
---
# <a name="how-to-update-the-status-bar"></a>Как выполнить Обновление строки состояния
**Строки состояния** находится на панели элементов управления в нижней части многие приложения windows, содержащий один или несколько строк текста состояния или индикаторы.  
  
## <a name="to-update-the-status-bar"></a>Для обновления строки состояния  
  
1.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> на каждый объект отдельного представления (DocView), предоставляемых редактора, таких как представление формы и представление кода.  
  
2.  При вызове метода интегрированной среды разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, обновить сведения в **строки состояния** , вызывая методы класса <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    >  Интегрированная среда разработки вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> только при первоначальной активации окна документа. В течение времени, который активен в окне документа, необходимо обновить **строки состояния** сведения, что состояние изменения редактора.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Объект **строки состояния** содержит четыре отдельные поля:  
  
- Текст состояния  
  
- Индикатор выполнения  
  
- Анимированный значок  
  
- Сведения о редакторе  
  
  Дополнительные сведения см. в разделе [строки состояния](/cpp/mfc/status-bars).  
  
  Интегрированная среда разработки автоматически вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> метод вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> реализации при активации окна документа.  
  
  Средство реализации VSPackage несет ответственность за обновление текст состояния в строке состояния. Интегрированной среды разработки сбрасывает эту строку, чтобы «ГОТОВ», если в текстовом поле состояния имеет значение пустой текст ("») во время простоя.  
  
## <a name="see-also"></a>См. также  
 [Строки состояния](/cpp/mfc/status-bars)