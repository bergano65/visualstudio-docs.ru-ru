---
title: Справочник по параметрам учетных записей
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db54590e6fa53caab56844947e5a699326dd99d2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846877"
---
# <a name="accounts-environment-options-dialog-box"></a>Страница "Учетные записи", папка "Среда", диалоговое окно "Параметры"

На этой странице вы можете настроить разные параметры для учетных записей, которые используются для входа в Visual Studio.

## <a name="personalization-account"></a>Учетная запись персонализации

### <a name="synchronize-settings-across-devices"></a>Синхронизация параметров между несколькими устройствами

Этот параметр определяет, нужно ли выполнять синхронизацию параметров между несколькими компьютерами. Дополнительные сведения см. в статье о [синхронизации параметров](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Включить поток кода устройства

Этот параметр изменяет поведение Visual Studio при выборе действия **Добавить учетную запись** на странице **Файл** > **Параметры учетной записи**. Вместо страницы **Вход в учетную запись** вы увидите диалоговое окно с URL-адресом и кодом, которые нужно вставить в адресную строку браузера для входа в систему. Этот вариант полезен в тех случаях, когда в Visual Studio невозможно войти обычным образом, например, если вы используете старую версию Internet Explorer или доступ ограничен брандмауэром. Дополнительные сведения см. в статье [Work with multiple user accounts](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow) (Работа с несколькими учетными записями пользователей).

## <a name="registered-azure-clouds"></a>Зарегистрированные облака Azure

В этом разделе отображаются экземпляры облака Azure, к которым у вас есть доступ через одну или несколько учетных записей, используемых для входа в Visual Studio. Например, у вас может быть доступ к частному экземпляру Azure в корпоративном центре обработки данных. Возможно также наличие доступа к экземпляру Azure независимой или государственной организации, например для правительства США или Китая. По умолчанию в этом списке всегда отображается экземпляр глобального облака Azure и вы не сможете его удалить.

Чтобы зарегистрировать дополнительное облако Azure, нажмите кнопку **Добавить**. Откроется диалоговое окно **Добавить новое облако Azure** со списком из нескольких хорошо известных экземпляров облака Azure, к которым вы можете подключиться. Также вы можете ввести URL-адрес частной конечной точки Azure.

![Добавить новый экземпляр облака Azure](media/add-new-azure-cloud.png)

После регистрации дополнительного облака Azure вы сможете выбирать нужное облако Azure при входе в Visual Studio.

## <a name="see-also"></a>См. также

- [Синхронизация параметров Visual Studio на нескольких компьютерах](../synchronized-settings-in-visual-studio.md)
- [Вход в Visual Studio](../signing-in-to-visual-studio.md)
- [Работа с несколькими учетными записями пользователя](../work-with-multiple-user-accounts.md)
- [Параметры среды](../environment-settings.md)
- [Диалоговое окно "Параметры среды"](../../ide/reference/environment-options-dialog-box.md)