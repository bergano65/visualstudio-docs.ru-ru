---
title: Программирование с помощью Инструментов Visual Studio для Unity и Azure | Документы Майкрософт
description: Программирование с помощью Инструментов Visual Studio для Unity и Azure. Azure предоставляет масштабируемое решение для хранения данных телеметрии и других данных игры в облаке.
ms.custom: ''
ms.date: 12/18/2017
ms.reviewer: crdun
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 7921D4C7-5526-42F5-8E03-82D3E33A893F
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 5be430b4a59dd4aa36945555f6553f321b9d50c0
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039824"
---
# <a name="program-with-unity-and-azure"></a>Программирование с Unity и Azure

Azure предоставляет масштабируемое решение для хранения данных телеметрии и других данных игры в облаке. Реализованная в выпуске Unity 2017 экспериментальная поддержка .NET 4.6 еще больше упростила интеграцию с Azure с помощью пакетов SDK для Azure .NET.

## <a name="experimental-azure-sdks"></a>Экспериментальные пакеты SDK для Azure

> [!NOTE]
> Эти пакеты SDK не поддерживаются, но предоставляются для ознакомления с реализованной в Unity экспериментальной поддержкой .NET 4.6.

В [песочнице](/sandbox/) вы сможете поработать со следующими экспериментальными пакетами SDK для Azure с помощью Unity:

* [пакет SDK для хранилища Azure для Unity](/sandbox/gamedev/unity/azure-storage-unity?wt.mc_id=azgamedev-sandbox-brpeek);
* [Пакет SDK для центров событий Azure для Unity](/sandbox/gamedev/unity/azure-event-hubs-unity?WT.mc_id=azgamedev-sandbox-brpeek);
* [пакет SDK для мобильных приложений Azure для Unity](/sandbox/gamedev/unity/azure-mobile-apps-unity?WT.mc_id=azgamedev-sandbox-brpeek).

## <a name="azure-sdk-sample"></a>Пример пакета SDK для Azure

Также доступен [простой пример игры](/sandbox/gamedev/unity/samples/azure-mobile-apps-unity-racer) с использованием пакета SDK для простых таблиц Azure и Unity. В игре используется хранилище данных простых таблиц Azure для отслеживания списка лидеров и хранения данных телеметрии игры. Сама игра доступна для [загрузки на портале GitHub](https://github.com/BrianPeek/AzureSamples-Unity).

![Снимок экрана с образцом игры](media/vstu_azure-test-sample-game-image2.png)
