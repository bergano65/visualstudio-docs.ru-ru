---
title: Отладка опубликованной облачной службы с помощью Visual Studio и IntelliTrace Azure | Документация Майкрософт
description: Узнайте, как выполнить отладку облачной службы с помощью Visual Studio и IntelliTrace
author: mikejo5000
manager: douge
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 865642bb7c8e41f81ff4b44ce628082e19b63a56
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002947"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Отладка опубликованной облачной службы Azure с помощью IntelliTrace и Visual Studio
С помощью IntelliTrace вы можете войти расширенные отладочные сведения для экземпляра роли, когда оно работает в Azure. Если вам необходимо найти причину проблемы, можно использовать журналы IntelliTrace для пошагового выполнения кода из Visual Studio, как если бы оно было запущено в Azure. По сути IntelliTrace записывает выполнение ключевого кода и данных среды при приложение Azure работает как облачной службы в Azure и позволяет воспроизводить записанные данные из Visual Studio. 

Можно использовать IntelliTrace, если у вас установлен выпуск Visual Studio Enterprise и ваше приложение Azure предназначено для .NET Framework 4 или более поздней версии. IntelliTrace собирает сведения о ролях Azure. Виртуальные машины для этих ролей всегда выполняться 64-разрядных операционных системах.

Кроме того, можно использовать [удаленной отладки](http://go.microsoft.com/fwlink/p/?LinkId=623041) для непосредственного подключения к облачной службе, запущенной в Azure.

> [!IMPORTANT]
> IntelliTrace предназначена только для отладочных сценариев и не должны использоваться для развертывания в рабочей среде.
> 

## <a name="configure-an-azure-application-for-intellitrace"></a>Настройка приложения Azure для IntelliTrace
Чтобы включить IntelliTrace для приложения Azure, необходимо создать и опубликовать приложение из проекта Azure для Visual Studio. Необходимо настроить IntelliTrace для приложения Azure, перед его публикацией в Azure. Если вы опубликовали приложение без настройки IntelliTrace, необходимо повторно опубликовать этот проект. Дополнительные сведения см. в разделе [публикации облачной службы с помощью Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=623012).

1. Когда вы готовы к развертыванию приложения Azure, убедитесь, что целевых объектов построения задано **Отладка**.

1. В **обозревателе решений**, щелкните правой кнопкой мыши проект и в контекстном меню выберите **публикации**.
   
1. В **опубликовать приложение Azure** диалоговое окно, выберите подписку Azure и выберите **Далее**.

1. В **параметры** выберите **Дополнительные параметры** вкладки.

1. Включите **включить IntelliTrace** параметр, чтобы собирать журналы IntelliTrace для приложения при его публикации в облаке.
   
1. Чтобы настроить базовую конфигурацию IntelliTrace, выберите **параметры** рядом с полем **включить IntelliTrace**.

    ![Ссылку "параметры IntelliTrace"](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)
   
1. В **параметры IntelliTrace** диалоговом окне можно указать какие события в журнал, требуется ли осуществлять сбор сведений о вызовах, каких модулей и процессов необходимо записывать журналы и какой объем места для записи. Дополнительные сведения об IntelliTrace см. в разделе [отладки с помощью IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=214468).
   
    ![Параметры IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

Журнал IntelliTrace представляет собой кольцевой файл журнала максимального размера, указанного в настройках IntelliTrace (размер по умолчанию — 250 МБ). Журналы IntelliTrace записываются в файл в файловой системе виртуальной машины. Когда вы запрашиваете журналы, моментальный снимок берется в определенный момент времени и загружается на локальный компьютер.

После публикации облачной службы Azure в Azure можно определить, был ли включен IntelliTrace из узла Azure в **обозревателя серверов**, как показано на следующем рисунке:

![Обозреватель сервера — IntelliTrace включен](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Загрузить журналы IntelliTrace для экземпляра роли
Visual Studio можно загрузить журналы IntelliTrace для экземпляра роли, выполнив следующие действия:

1. В **обозревателя серверов**, разверните **облачных служб** узел и найдите экземпляр роли, журналы которых вы хотите скачать. 

1. Щелкните правой кнопкой мыши экземпляр роли и в контекстном меню, выберите **Просмотр журналов IntelliTrace**. 

    ![Просмотр журналов IntelliTrace пункт меню](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. Журналы IntelliTrace будут загружены в файл в каталоге на локальном компьютере. Заносит в журнал при каждом запросе IntelliTrace, создается новый моментальный снимок. Во время загрузки журналов Visual Studio отображает ход выполнения операции в **журнал действий Azure** окна. Как показано на следующем рисунке, можно развернуть элемент строку для операции просмотреть подробные сведения.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

Можно продолжать работу в Visual Studio во время загрузки журналов IntelliTrace. После завершения загрузки журнала он открывается в Visual Studio.

> [!NOTE]
> Журналы IntelliTrace могут содержать исключения, которые платформа создает и в дальнейшем обрабатывает. Эти исключения в составе обычном запуске роли, поэтому можно обращать внимания их формируются внутренним кодом платформы.
> 
> 

## <a name="next-steps"></a>Следующие шаги
- [Параметры отладки облачных служб Azure](vs-azure-tools-debugging-cloud-services-overview.md)
- [Публикация облачной службы Azure с помощью Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)