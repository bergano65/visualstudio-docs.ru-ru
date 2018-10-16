---
title: 'Практическое: подключение к данным в службе | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce851a864dd11759c36c7ae6cb275e9e71cd11a1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301799"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Практическое руководство. Подключение к данным в службе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Подключение приложения к данным, возвращаемым службой, выполнив [мастер настройки источника данных](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) и выбрав **службы** на **Выбор типа источника данных**страницы.  
  
 После завершения работы мастера, добавляется в проект ссылку на службу и немедленно становится доступной в [окна "Источники данных"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
> [!NOTE]
>  Элементы, отображаемые в **источников данных** окне зависят от информации, возвращаемой службой. Некоторые службы могут не предоставлять достаточных сведений для **мастер настройки источника данных** создал объекты. Например, если служба возвращает нетипизированный набор данных, затем элементы не отображаются в **окна "Источники данных"** после завершения работы мастера. Это потому, что нетипизированные наборы данных не предусматривают схемы, поэтому мастер не имеет достаточно сведений для создания источника данных.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>Для подключения приложения к службе  
  
1.  В меню **Данные** выберите команду **Добавить новый источник данных**.  
  
2.  Выберите **службы** на **Выбор типа источника данных** странице, а затем выберите **Далее**.  
  
3.  Введите адрес службы, которую требуется использовать, или нажмите кнопку **Discover** найдите службы в текущем решении, а затем нажмите кнопку **Go**.  
  
4.  При необходимости новый **пространства имен** можно ввести вместо значения по умолчанию.  
  
    > [!NOTE]
    >  Нажмите кнопку **Дополнительно** открыть [Настройка службы ссылку на диалоговое окно](../data-tools/configure-service-reference-dialog-box.md).  
  
5.  Нажмите кнопку **ОК** для добавления ссылки на службу в проект.  
  
6.  Нажмите кнопку **Готово**.  
  
     Источник данных добавляется к **источников данных** окна.  
  
## <a name="next-steps"></a>Следующие шаги  
  
#### <a name="to-add-functionality-to-your-application"></a>Добавление функциональности в приложение  
  
-   Выберите элемент в **источников данных** окна и перетащите его на форму для создания связанных элементов управления. Дополнительные сведения см. в разделе [привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Привязка элементов управления WPF к службе данных WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Службы Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

