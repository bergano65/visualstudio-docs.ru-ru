---
title: "Как: подключение к данным в службе | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 334f31dcd68e031bfb25b4e0dcd6ce55b9d2f20c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-connect-to-data-in-a-service"></a>Практическое руководство. Подключение к данным в службе
Подключение приложения к данным, возвращаемым службой, запустив [мастер настройки источника данных](../data-tools/media/data-source-configuration-wizard.png) и выбрав **службы** на **Выбор типа источника данных**страницы.  
  
 После завершения работы мастера ссылка на службу добавляется в проект и немедленно становится доступной в [окно "Источники данных"](add-new-data-sources.md).  
  
> [!NOTE]
>  Элементы, отображаемые в **источники данных** , зависят от информации, которую возвращает служба. Некоторые службы могут не предоставлять достаточно информации для **мастер настройки источника данных** создал объекты. Например, если служба возвращает нетипизированный набор данных, затем элементы не отображаются в **окно "Источники данных"** после завершения работы мастера. Это потому, что нетипизированные наборы данных не предусматривают схемы, поэтому мастер не имеет достаточных сведений для создания источника данных.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>Чтобы подключить приложение к службе  
  
1.  В меню **Данные** выберите команду **Добавить новый источник данных**.  
  
2.  Выберите **службы** на **Выбор типа источника данных** и нажмите кнопку **Далее**.  
  
3.  Введите адрес службы, которую требуется использовать, или нажмите кнопку **Discover** поиска служб в текущем решении, а затем нажмите кнопку **Go**.  
  
4.  При необходимости новый **имен** можно ввести вместо значения по умолчанию.  
  
    > [!NOTE]
    >  Нажмите кнопку **Дополнительно** Открытие [настроить ссылку диалоговое окно службы](../data-tools/configure-service-reference-dialog-box.md).  
  
5.  Нажмите кнопку **ОК** для добавления ссылки на службу в проект.  
  
6.  Нажмите кнопку **Готово**.  
  
     Источник данных добавляется к **источники данных** окна.  
  
## <a name="next-steps"></a>Дальнейшие действия  
  
#### <a name="to-add-functionality-to-your-application"></a>Добавление функциональности в приложение  
  
-   Выберите элемент в **источники данных** окна и перетащите его в форму, чтобы создать элементы управления с привязкой. Дополнительные сведения см. в разделе [привязки элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Привязка элементов управления WPF к службе данных WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Службы Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)