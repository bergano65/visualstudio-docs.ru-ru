---
ms.technology: vs-ai-tools
ms.openlocfilehash: 875bd78f6e1c6298d7f94360363dcf731cc3e992
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874440"
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