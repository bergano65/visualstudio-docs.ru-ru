---
title: "Инструменты Visual Studio для Unity. Пошаговое руководство по ресурсам игры в Azure | Документы Майкрософт"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: C06FAB2E-F592-4EFF-B96A-58858C92DCEB
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 3b1ad3d7dc6af48986e8b10278a8b8135843239d
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="import-sample-game-assets"></a>Импорт ресурсов образца игры

Теперь, когда основные функциональные возможности были протестированы и испытаны в работе, пора импортировать ресурсы образца игры.

## <a name="import-package"></a>Импорт пакета

1. Скачайте [пакет с ресурсами образца игры](https://github.com/dantogno/UnityAzureSample/blob/master/Azure%20Easy%20tables%20sample%20game%20assets.unitypackage).

2. Убедитесь в том, что проект Unity открыт, а затем перейдите к месту, куда был скачан пакет, и дважды щелкните файл. В Unity откроется диалоговое окно импорта.

3. Щелкните **All** (Все), а затем нажмите кнопку **Import** (Импорт). Подождите, пока индикатор выполнения дойдет до конца.

  ![Импорт пакета](media/vstu_azure-import-sample-assets-image1.png)

## <a name="add-scenes-to-build-settings"></a>Добавление сцен в параметры сборки

Когда импорт файлов завершится, необходимо добавить требуемые файлы сцен в параметрах сборки проекта Unity.

1. В окне проекта Unity перейдите в каталог **Azure Easy Tables sample game assets/Scenes**.

2. В меню Unity выберите **File > Build Settings...** (Файл > Параметры сборки...). Откроется диалоговое окно параметров сборки.

3. Перетащите файлы **HeatmapScene**, **LeaderboardScene**, **MenuScene** и **RaceScene** из окна проекта в раздел **Scenes In Build** (Сцены в сборке) диалогового окна "Build Settings" (Параметры сборки).

  ![Импорт пакета](media/vstu_azure-import-sample-assets-image2.png)

4. В меню Unity выберите **File > Save Project** (Файл > Сохранить проект), чтобы сохранить параметры сборки.

## <a name="next-step"></a>Дальнейшие действия

* [Тестирование образца игры](visual-studio-tools-for-unity-azure-game.md)