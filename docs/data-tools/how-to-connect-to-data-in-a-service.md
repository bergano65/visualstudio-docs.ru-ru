---
title: Практическое руководство. Подключение к данным в службе
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0affe931e5b85d32acdc95fecaa50f3b7f2fe8f4
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2018
ms.locfileid: "39175703"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Практическое: подключение к данным в службе

Подключение приложения к данным, возвращаемым службой, выполнив [мастер настройки источника данных](../data-tools/media/data-source-configuration-wizard.png) и выбрав **службы** на **Выбор типа источника данных**страницы.

После завершения работы мастера, добавляется в проект ссылку на службу и немедленно становится доступной в [окна "Источники данных"](add-new-data-sources.md).

> [!NOTE]
> Элементы, отображаемые в **источников данных** окне зависят от информации, возвращаемой службой. Некоторые службы могут не предоставлять достаточных сведений для **мастер настройки источника данных** создал объекты. Например, если служба возвращает нетипизированный набор данных, элементы не отображаются в **окна "Источники данных"** после завершения работы мастера. Это потому, что нетипизированные наборы данных не предусматривают схемы, поэтому мастер не имеет достаточно сведений для создания источника данных.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Для подключения приложения к службе

1.  В меню **Данные** выберите команду **Добавить новый источник данных**.

2.  Выберите **службы** на **Выбор типа источника данных** странице, а затем выберите **Далее**.

3.  Введите адрес службы, которую требуется использовать, или нажмите кнопку **Discover** найдите службы в текущем решении, а затем нажмите кнопку **Go**.

4.  При необходимости можно ввести новый **пространства имен** вместо значения по умолчанию.

    > [!NOTE]
    > Нажмите кнопку **Дополнительно** открыть [настроить ссылку на службу-диалоговое окно](../data-tools/configure-service-reference-dialog-box.md).

5.  Нажмите кнопку **ОК** для добавления ссылки на службу в проект.

6.  Нажмите кнопку **Готово**.

     Источник данных добавляется к **источников данных** окна.

## <a name="next-steps"></a>Следующие шаги

Добавление функциональных возможностей приложения, выберите элемент в **источников данных** окна и перетащите его на форму для создания связанных элементов управления. Дополнительные сведения см. в разделе [привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>См. также

- [Привязка элементов управления WPF к службе данных WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Службы данных службы Windows Communication Foundation и WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)