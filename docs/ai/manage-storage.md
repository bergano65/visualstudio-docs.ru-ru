---
title: Обзор хранилища для отправки данных
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 188ebee353261ba49f6677a0f96db68b7e8d46d9
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371616"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Обзор хранилища для отправки данных или загрузки моделей и журналов

Вы можете использовать функцию обзора всего хранилища на удаленном компьютере или в общей папке Azure для отправки данных или загрузки моделей и журналов. Или, если вам необходимы журналы и выходные данные определенного задания, они также доступны вам в обозревателе заданий.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Доступ ко всем данным на удаленном компьютере или в общей папке

1. Откройте **Обозреватель сервера**.
2. Разверните контекст удаленного компьютера или вычислений Batch AI.
3. Щелкните правой кнопкой мыши **Хранилище**, а затем **Обзор**.

    ![storage](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Доступ к данным конкретного задания на удаленном компьютере или в общей папке

1. Откройте [Журнал заданий](job-details.md)
2. Выберите задание.
3. Щелкните **Рабочая папка** или **StdOut/Stderr** для быстрого доступа к важным файлам журнала.

    ![storage](media/manage-storage/job-workingfolder.png)
