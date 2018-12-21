---
title: Удаление Visual Studio
titleSuffix: ''
description: Пошаговые инструкции по полному удалению Visual Studio с компьютера.
ms.custom: seodec18
ms.date: 09/12/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb3f86c59f205137dc3b72c8f0beff69f4d95a99
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159663"
---
# <a name="remove-visual-studio-2017"></a>Удаление Visual Studio 2017

Если произошла неустранимая ошибка, из-за которой невозможно восстановить или удалить Visual Studio, вы можете запустить средство `InstallCleanup.exe`, чтобы удалить файлы установки и сведения о продукте для всех установленных экземпляров Visual Studio 2017 и более поздних версий. Запуск этого средства следует рассматривать как крайнюю меру в случае, если не удается восстановить или удалить среду, так как оно может удалить компоненты из других установок Visual Studio или других продуктов, которые нужно восстановить.

При выполнении приведенных ниже инструкций средство можно запускать с различными параметрами командной строки, которые определяют следующее поведение:

| Параметр | Поведение |
| ------ | -------- |
| `-i`   | Этот параметр используется по умолчанию, если не переданы другие параметры. Он приводит к удалению только главного каталога установки и сведений о продукте. Такое поведение является предпочтительным, если после запуска средства `InstallCleanup.exe` вы планируете установить ту же версию. |
| `-f`   | При указании этого параметра удаляются главный каталог установки, сведения о продукте и большинство других компонентов, которые установлены вне каталога установки и могут использоваться другими экземплярами Visual Studio или иными продуктами. Это поведение является предпочтительным, если вы планируете удалить среду Visual Studio и не устанавливать ее повторно. |

1. Закройте установщик Visual Studio.
2. Откройте командную строку от имени учетной записи администратора. Чтобы открыть командную строку с правами администратора, выполните указанные ниже действия.
   * Откройте меню **Пуск**.
   * Наберите команду **cmd**.
   * Щелкните правой кнопкой мыши пункт **Командная строка**и выберите команду **Запуск от имени администратора**.
3. Введите полный путь к служебной программе `InstallCleanup.exe` и передайте в командной строке требуемые параметры. По умолчанию эта программа расположена по следующему адресу:
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

Если вы не нашли файл `InstallCleanup.exe` в каталоге установщика Visual Studio, который всегда находится в `%ProgramFiles(x86)%\Microsoft Visual Studio`, следуйте инструкциям по [установке Visual Studio](install-visual-studio.md). Когда появится экран выбора рабочей нагрузки, закройте окно и выполните описанные выше действия снова.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка Visual Studio 2017](install-visual-studio.md)
* [Обновление Visual Studio 2017](update-visual-studio.md)
* [Изменение Visual Studio 2017](modify-visual-studio.md)
* [Удаление Visual Studio 2017](uninstall-visual-studio.md)
