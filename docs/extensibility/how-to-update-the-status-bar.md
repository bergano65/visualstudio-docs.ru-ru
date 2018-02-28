---
title: "Как: обновление строки состояния | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 76801810aafa3bd4048776ca38385ad1cf508d94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-update-the-status-bar"></a>Как: обновление строки состояния
**Строка состояния** находится панель элементов управления в нижней части многих приложений windows, содержащий один или несколько строк текста состояния или индикаторы.  
  
### <a name="to-update-the-status-bar"></a>Для обновления строки состояния  
  
1.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> для каждого отдельного представления объекта (DocView), предоставляющий редактора, таких как представление формы и представление кода.  
  
2.  При вызове метода IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, обновить сведения в **строка состояния** , вызвав методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    >  Интегрированная среда разработки вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> только при первоначальной активации окна документа. В течение времени, которое является активной в окне документа, необходимо обновить **строка состояния** сведения, что состояние изменения редактора.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Объект **строка состояния** содержит четыре отдельные поля:  
  
-   Текст состояния  
  
-   Индикатор выполнения  
  
-   Анимированный значок  
  
-   Сведения о редакторе  
  
 Дополнительные сведения см. в разделе [строки состояния](/cpp/mfc/status-bars).  
  
 Интегрированная среда разработки автоматически вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> метод вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> реализации при активации окна документа.  
  
 Разработчик VSPackage, отвечает за обновление текст состояния в строке состояния. IDE сбрасывает эту строку, чтобы все «ГОТОВО», если текстовое поле состояния имеет значение пустой текст ("») в состоянии простоя.  
  
## <a name="see-also"></a>См. также  
 [Строки состояния](/cpp/mfc/status-bars)