---
title: "Инструменты Visual Studio для Unity. Пошаговое руководство по работе с Azure | Документы Майкрософт"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7921D4C7-5526-42F5-8E03-82D3E33A893F
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: d5242dd873591abee15f528d09b6f588ea12f5ba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="using-azure-easy-tables-with-unity-walkthrough"></a>Пошаговое руководство по использованию простых таблиц Azure с Unity

![Снимок экрана с образцом игры](media/vstu_azure-test-sample-game-image2.png)

## <a name="introduction"></a>Вступление

Azure предоставляет масштабируемое решение для хранения данных телеметрии и других данных игры в облаке. Появившаяся в выпуске Unity 2017 поддержка .NET 4.6 еще более упростила интеграцию с Azure с помощью пакета SDK Azure Mobile Client.

Ниже приводятся пошаговые инструкции по настройке проекта Unity, в котором платформа Azure используется для сохранения данных телеметрии и списка лидеров в облаке.

> [!NOTE]
> Для этого проекта требуется экспериментальная среда выполнения скриптов .NET 4.6 Mono в Unity 2017. [Компания Unity объявила, что вскоре эта среда станет стандартным компонентом](https://forum.unity3d.com/threads/future-plans-for-the-mono-runtime-upgrade.464327/), однако пока она помечена как экспериментальная и при работе с ней могут возникать проблемы.

> В этом пошаговом руководстве приводится пример для подключения к интерфейсу мобильных приложений Azure из сборки Unity на ПК. На момент написания данного документа существовали известные проблемы, препятствующие работе этого проекта на платформах Mac и Android. Хотя эти проблемы будут устранены, точный срок неизвестен. Дополнительные сведения можно найти на форуме Unity, посвященном [экспериментальной среде сценариев](https://forum.unity3d.com/forums/experimental-scripting-previews.107/).

## <a name="download-the-completed-project"></a>Скачивание готового проекта

Готовый проект доступен в GitHub. Однако в этом руководстве предполагается, что вы начинаете работу с пустого проекта. По мере необходимости будут приводиться ссылки для скачивания ресурсов.

## <a name="walkthrough-steps"></a>Этапы пошагового руководства

1. [Настройка простых таблиц в Azure](visual-studio-tools-for-unity-azure-configure.md)
2. [Создание простых таблиц](visual-studio-tools-for-unity-azure-setup.md)
3. [Подготовка среды разработки](visual-studio-tools-for-unity-azure-prepare.md)
4. [Создание классов моделей данных](visual-studio-tools-for-unity-azure-data.md)
5. [Реализация Azure MobileServiceClient](visual-studio-tools-for-unity-azure-mobile-client.md)
6. [Обновление хранилища сертификатов безопасности Unity Mono](visual-studio-tools-for-unity-azure-security.md)
7. [Тестирование клиентских подключений](visual-studio-tools-for-unity-azure-connection.md)
7. [Импорт ресурсов образца игры](visual-studio-tools-for-unity-azure-game-assets.md)
8. [Тестирование образца игры](visual-studio-tools-for-unity-azure-game.md)
9. [Сведения о RaceScene](visual-studio-tools-for-unity-azure-racescene.md)
10. [Сведения о HeatmapScene](visual-studio-tools-for-unity-azure-heatmapscene.md)
11. [Сведения о LeaderboardScene](visual-studio-tools-for-unity-azure-leaderboardscene.md)


## <a name="next-step"></a>Дальнейшие действия
* [Настройка простых таблиц в Azure](visual-studio-tools-for-unity-azure-configure.md)
