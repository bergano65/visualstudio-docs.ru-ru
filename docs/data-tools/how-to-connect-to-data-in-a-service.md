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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f3fd643ca29c5f5e4df20f244bc06b6bca04b9bd
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930744"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Практическое руководство. Подключение к данным в службе

Подключение приложения к данным, возвращаемым службой, выполнив [мастер настройки источника данных](../data-tools/media/data-source-configuration-wizard.png) и выбрав **службы** на **Выбор типа источника данных**страницы.

После завершения работы мастера, добавляется в проект ссылку на службу и немедленно становится доступной в [окна "Источники данных"](add-new-data-sources.md#data-sources-window).

> [!NOTE]
> Элементы, которые отображаются в окне **Источники данных**, зависят от информации, возвращаемой службой. Некоторые службы могут предоставлять недостаточный объем информации для того, чтобы **Мастер настройки источника данных** создал объекты с возможностью привязки. Например, если служба возвращает нетипизированный набор данных, элементы не отображаются в **источников данных** окне после завершения работы мастера. Это потому, что нетипизированные наборы данных не предусматривают схемы, поэтому мастер не имеет достаточно сведений для создания источника данных.

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

     Источник данных добавлен в окно **Источники данных**.

## <a name="next-steps"></a>Следующие шаги

Добавление функциональных возможностей приложения, выберите элемент в **источников данных** окна и перетащите его на форму для создания связанных элементов управления. Дополнительные сведения см. в разделе [привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>См. также

- [Привязка элементов управления WPF к службе данных WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Службы Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)