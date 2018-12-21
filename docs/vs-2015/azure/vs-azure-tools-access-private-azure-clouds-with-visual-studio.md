---
title: Доступ к частным облакам Azure с помощью Visual Studio | Документация Майкрософт
description: Узнайте, как получить доступ к ресурсам частного облака с помощью Visual Studio.
author: ghogen
manager: douge
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 216b85e0ebf42b79c388ce217d548f2dce3c86b6
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002964"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>Доступ к частным облакам Azure с помощью Visual Studio

По умолчанию Visual Studio поддерживает конечные точки REST облаков Azure. В этой статье вы узнаете, как использовать сертификат частного облака для обращения и взаимодействия с частным облаком из Visual Studio.

1. На портале Azure для частного облака скачайте файл параметров публикации или обратитесь к администратору для файла параметров публикации. (Файл с расширением `.publishsettings`.)

1. В Visual Studio **обозревателя серверов**, щелкните правой кнопкой мыши **Azure** узел и выберите **управление подписками и их фильтрация**.

    ![Управление подписками команды](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. В **управление подписками Microsoft Azure** диалоговом окне выберите **сертификаты** , а затем установите **импорта**.

    ![Импорт сертификатов Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. В **Импорт подписок Microsoft Azure** диалоговом окне выберите **Обзор**.

    ![Кнопка в диалоговом окне Импорт подписок Microsoft Azure "Обзор"](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. В **откройте** диалоговое окно, перейдите в каталог, где был сохранен файл параметров публикации, выберите файл, а затем выберите **откройте**.

    ![Выберите файл параметров публикации](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. Вернувшись в **Импорт подписок Microsoft Azure** диалоговом окне выберите **импорта**.

    ![Импортировать файл параметров публикации](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    Сертификаты импортируются из PUBLISHSETTINGS файла в Visual Studio, и теперь вы можете работать с ресурсами частного облака.

