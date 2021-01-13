---
title: Отслеживание с помощью TensorBoard
description: Сведения о том, как визуально отслеживать процесс обучения модели с помощью TensorBoard в Visual Studio.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 650189c4418355ae06b296bac7e16eece0ea88ad
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727259"
---
# <a name="monitor-with-tensorboard"></a>Отслеживание с помощью TensorBoard

TensorBoard позволяет визуально отслеживать процесс обучения модели.

1. Щелкните проект правой кнопкой мыши и выберите **Запуск TensorBoard**, а затем укажите каталог для журналов TensorBoard с выходными данными.

    ![Снимок экрана: Обозреватель решений Visual Studio с выбранным проектом MNIST. Также открыто контекстное меню, и выделена команда Run TensorBoard (Запуск TensorBoard).](media/monitor-tensorboard/run-tensorboard.png)

2. Обратите внимание на уменьшение числа ошибок со временем, что означает повышение качества.

    ![Снимок экрана: основное окно TensorBoard с графическими визуализациями данных из журналов TensorBoard.](media/monitor-tensorboard/tensorboard.png)
