---
title: Дистанционное отладка проекта СЗЗ Документы Майкрософт
ms.custom: remotedebugging
ms.date: 08/14/2018
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 0173ed557afa47129e0cc92d9ef9b2d94a7b198f
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301089"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Дистанционное отладка проекта СЗ в визуальной студии
Чтобы отладить приложение Visual Studio на другом компьютере, установите и запустите удаленные инструменты на компьютере, где вы развернете приложение, направьте проект для подключения к удаленному компьютеру из Visual Studio, а затем разместите и запустите приложение.

![Компоненты дистанционного отладчика](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Для получения информации об удаленной отладке универсальных приложений Windows (UWP) [см.](debug-installed-app-package.md)

## <a name="requirements"></a>Требования

Удаленный отладчик поддерживается на Windows 7 и более новых (не телефон) и версии Windows Server, начиная с Windows Server 2008 Service Pack 2. Полный список требований [можно](../debugger/remote-debugging.md#requirements_msvsmon)узнать на примере требований.

> [!NOTE]
> Отладка между двумя компьютерами, подключенными через прокси, не поддерживается. Не рекомендуется отладка из-за высокой задержки или соединения с низкой пропускной способностью, например, в Интернете или через Интернет в разных странах, и она может вывести из строя или быть неприемлемо медленной.

## <a name="download-and-install-the-remote-tools"></a>Скачивание и установка инструментов удаленной отладки

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> В некоторых сценариях наиболее эффективным может быть запуск удаленного отладчика от общего файла. Для получения дополнительной информации [см. Выполнить удаленный отладчик из общего файла общего обмена](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a>Настройка удаленного отладчика

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Если вам необходимо добавить разрешения для дополнительных пользователей, измените режим проверки подлинности или номер порта для удаленного [отладчика, см.](../debugger/remote-debugging.md#configure_msvsmon)

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a>Дистанционное отладка проекта СЗЗ
 В следующей процедуре, имя и путь проекта Является C: «remotetemp»MyMfc, и имя удаленного компьютера **MJO-DL**.

1. Создайте приложение MFC с именем **mymfc**.

2. Создайте точку останова в легкодоступном месте приложения, например в файле **MainFrm.cpp**, в начале `CMainFrame::OnCreate`.

3. В Solution Explorer нажмите правой кнопкой мыши на проект и выберите **Свойства.** Откройте вкладку **Отладка**.

4. Для параметра **Загружаемый отладчик** задайте значение **Удаленный отладчик Windows**.

    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")

5. Внесите в свойства следующие изменения:

   |Параметр|Значение|
   |-|-|
   |Удаленная команда|C:\remotetemp\mymfc.exe|
   |Рабочий каталог|C:\remotetemp|
   |Имя удаленного сервера|MJO-DL:*номер*|
   |Соединение|Удаленный доступ с аутентификацией Windows|
   |Тип отладчика|Только машинный код|
   |Каталог развертывания|C:\remotetemp.|
   |Дополнительные файлы развертывания|C:\data\mymfcdata.txt.|

    При развертывании дополнительных файлов (необязательно), папка должна существовать на обеих машинах.

6. В Solution Explorer нажмите правой кнопкой мыши и выберите **диспетчер конфигурации.**

7. Для конфигурации **Отладка** установите флажок **Развертывание**.

    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. Начните отладку (выберите **Отладка > Начать отладку** или нажмите клавишу **F5**).

9. Исполняемый файл автоматически развернется на удаленном компьютере.

10. Если это вызвано, введите учетные данные сети для подключения к удаленному компьютеру.

     Необходимые учетные данные специфичны для конфигурации безопасности вашей сети. Например, на доменном компьютере можно выбрать сертификат безопасности или ввести доменное имя и пароль. На машине, не входящих в домен, вы можете <strong>MJO-DL\name@something.com</strong>ввести имя машины и действительное имя учетной записи пользователя, как, наряду с правильным паролем.

11. На компьютере с Visual Studio вы должны увидеть, что выполнение остановилось в точке останова.

    > [!TIP]
    > Кроме того, файлы можно развернуть как отдельный шаг. В **обозревателе решений** щелкните правой кнопкой мыши узел **mymfc** и выберите пункт **Развернуть**.

    Если у вас есть некодовые файлы, необходимые приложению, вы можете указать их в **дополнительных файлах для развертывания** на странице **удаленного отладчика Windows.**

    Кроме того, можно включить файлы в проект и установить свойство **содержимого** на странице **Да** на странице **Свойств для** каждого файла. Эти файлы копируются в **каталог развертывания,** указанный на странице **удаленного отладки Windows.** Вы также можете изменить **тип элемента** для **копирования файла** и указать дополнительные свойства там, если вам нужно, чтобы файлы были скопированы в подфайлник **каталога развертывания.**

## <a name="set-up-debugging-with-remote-symbols"></a>Настройка отладки с удаленными символами

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>См. также раздел
- [Отладка в Visual Studio](../debugger/index.yml)
- [Первый взгляд на отладчика](../debugger/debugger-feature-tour.md)
- [Настройка брандмауэра Windows для удаленной отладки](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) (Назначение портов для удаленного отладчика)
- [Удаленная отладка ASP.NET на удаленном компьютере IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Ошибки удаленной отладки и их устранение](../debugger/remote-debugging-errors-and-troubleshooting.md)