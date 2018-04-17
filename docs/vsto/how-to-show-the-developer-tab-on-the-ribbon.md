---
title: 'Как: Отображение вкладки разработчика на ленте | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9921c10d8a886eb4051b3d5f3d8392ddc77c2da7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Практическое руководство. Отображение вкладки разработчика на ленте
  Чтобы получить доступ к **разработчика** вкладку на ленте приложения Microsoft Office, необходимо настроить его, чтобы отобразить эту вкладку, так как он не отображается по умолчанию. Например, необходимо отобразить эту вкладку, если требуется добавить <xref:Microsoft.Office.Tools.Word.GroupContentControl> в настройку уровня документа для Word.  
  
> [!NOTE]  
>  Это руководство применимо только к приложениям Office 2010 или более поздней версии. Если вы хотите отобразить эту вкладку в системе Microsoft Office 2007, см. следующую версию этого раздела [как: Отображение вкладки разработчика на ленте](http://msdn.microsoft.com/library/bb608625(v=vs.90).aspx).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Не имеет доступа к **разработчика** вкладки.  
  
### <a name="to-show-the-developer-tab"></a>Отображение вкладки "Разработчик"  
  
1.  Запустите любое приложение Office, указанное в этом разделе. В разделе **применяется к:** Примечание ранее в этом разделе.  
  
2.  На **файл** выберите **параметры** кнопки.  
  
     На следующем рисунке показан **файл** вкладку и **параметры** кнопки в Office 2010.  
  
     ![При выборе файла, параметры в Outlook 2010](../vsto/media/vsto-office-file-tab.png "при выборе файла, параметры в Outlook 2010")  
  
     На следующем рисунке показан **файл** в Office 2013.  
  
     ![Вкладка "файл" в Outlook 2013](../vsto/media/vsto-office2013-filetab.png "вкладка "файл" в Outlook 2013")  
  
     На следующем рисунке показан **параметры** кнопки в Office 2013.  
  
     ![Кнопка "Параметры" в Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "кнопка "Параметры" в Outlook 2013 Preview")  
  
3.  В *ApplicationName *** параметры** диалогового окна выберите **настроить ленту** кнопки.  
  
     На следующем рисунке показан **параметры** диалоговое окно и **настроить ленту** кнопки в Excel 2010. Расположение этой кнопки аналогично и во всех остальных приложениях, перечисленных в приведенном выше подразделе "Применимо к".  
  
     ![Настройка ленты кнопку](../vsto/media/vsto-office2010-customizeribbonbutton.png "кнопку Настройка ленты")  
  
4.  В списке основных вкладок выберите **разработчика** флажок.  
  
     На следующем рисунке показан **разработчика** флажок в Word 2010 и [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Расположение этого флажка аналогично и во всех остальных приложениях, перечисленных в приведенном выше подразделе "Применимо к".  
  
     ![Флажок "Разработчик" в диалоговом окне Параметры Word](../vsto/media/vsto-office2010-developercheckbox.png "флажок "Разработчик" в диалоговом окне Параметры Word")  
  
5.  Выберите **ОК** кнопку, чтобы закрыть **параметры** диалоговое окно.  
  
## <a name="see-also"></a>См. также  
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)  
  
  