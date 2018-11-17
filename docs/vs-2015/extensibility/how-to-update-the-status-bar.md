---
title: 'Практическое: обновления строки состояния | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb70e8799b74f470a2216a63aae4637fe1872681
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768352"
---
# <a name="how-to-update-the-status-bar"></a>Практическое: обновления строки состояния
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Строки состояния** находится на панели элементов управления в нижней части многие приложения windows, содержащий один или несколько строк текста состояния или индикаторы.  
  
### <a name="to-update-the-status-bar"></a>Для обновления строки состояния  
  
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
  
  Дополнительные сведения см. в разделе [строки состояния](http://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e).  
  
  Интегрированная среда разработки автоматически вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> метод вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> реализации при активации окна документа.  
  
  Средство реализации VSPackage несет ответственность за обновление текст состояния в строке состояния. Интегрированной среды разработки сбрасывает эту строку, чтобы «ГОТОВ», если в текстовом поле состояния имеет значение пустой текст ("») во время простоя.  
  
## <a name="see-also"></a>См. также  
 [Строки состояния](http://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)

