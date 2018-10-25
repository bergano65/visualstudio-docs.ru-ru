---
title: 'Практическое: обновления строки состояния | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b7f7d52ad8dc75f8e8bd313794b44c231522cde7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829941"
---
# <a name="how-to-update-the-status-bar"></a>Практическое: обновления строки состояния
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