---
ms.technology: vs-ai-tools
ms.openlocfilehash: b941d0ba55c540de4bda1cb0f9c4ed18ceab524f
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
ms.locfileid: "29708281"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Обзор хранилища для отправки данных или загрузки моделей и журналов

Вы можете использовать функцию обзора всего хранилища на удаленном компьютере или в общей папке Azure для отправки данных или загрузки моделей и журналов. Или, если вам необходимы журналы и выходные данные определенного задания, они также доступны вам в обозревателе заданий

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Доступ ко всем данным на удаленном компьютере или в общей папке
1. Откройте **Обозреватель сервера**
2. Разверните контекст удаленного компьютера или вычислений Batch AI
3. Щелкните правой кнопкой мыши **Хранилище**, а затем — **Обзор**

    ![storage](media\manage-storage\browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Доступ к данным конкретного задания на удаленном компьютере или в общей папке
1. Откройте [Журнал заданий](job-details.md)
2. Выберите задание
3. Щелкните **Рабочая папка** или StdOut/Stderr для быстрого доступа к важным файлам журнала

    ![storage](media\manage-storage\job-workingfolder.png)
