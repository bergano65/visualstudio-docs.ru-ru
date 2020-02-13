---
title: Выполните вход в Visual Studio
titleSuffix: ''
ms.custom: seodec18
ms.date: 12/10/2018
ms.topic: conceptual
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: adda66bbccafa3c1d7f20d60a3f8ee0a4995353c
ms.sourcegitcommit: b2fc9ac7d73c847508f6ed082bed026476bb3955
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2020
ms.locfileid: "77027585"
---
# <a name="sign-in-to-visual-studio"></a>Выполните вход в Visual Studio

Процесс разработки в Visual Studio можно оптимизировать и персонализировать, если настроена учетная запись персонализации при входе в среду IDE.

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Информацию о Visual Studio для Mac см. в статье [Вход в Visual Studio для Mac](/visualstudio/mac/signing-in).

## <a name="why-should-i-sign-in-to-visual-studio"></a>Почему нужно выполнять вход в Visual Studio?

Выполняя вход, вы можете использовать расширенный спектр возможностей Visual Studio. Например, после входа вы, помимо прочего, можете [синхронизировать настройки](synchronized-settings-in-visual-studio.md) между устройствами, продлевать срок действия пробной версии и автоматически подключаться к службе Azure.

Ниже приведен полный список возможностей, которые вы получаете после входа:

- **Доступ к программе Visual Studio Dev Essentials**. Эта программа включает бесплатное программное обеспечение, обучение, поддержку и многое другое. Дополнительные сведения см. в разделе [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) .

- **Синхронизация параметров Visual Studio**. Настраиваемые параметры, например привязки клавиш, макет окна и цветовая тема, вступают в силу, как только вы войдете в Visual Studio на любом устройстве. См. раздел [Синхронизированные параметры в Visual Studio](../ide/synchronized-settings-in-visual-studio.md).

- **Разблокировка выпуска Visual Studio Community** — если установка выпуска Community запрашивает лицензию, войдите в интегрированную среду разработки, чтобы разблокировать выпуск самостоятельно.

- **Продление пробного периода Visual Studio**. Пробный период Visual Studio Professional и Visual Studio Enterprise продлевается с 30 до 90 дней.

- **Разблокировка Visual Studio при использовании учетной записи, связанной с подпиской Visual Studio или организацией Azure DevOps **. См. раздел [Разблокирование Visual Studio](../ide/how-to-unlock-visual-studio.md).

- **Автоматическое подключение к таким службам, как Azure и Azure DevOps Services**, в интегрированной среде разработки без повторного запроса учетных данных одной и той же учетной записи.

## <a name="how-to-sign-in-to-visual-studio"></a>Вход в Visual Studio

При первом открытии Visual Studio появляется запрос на вход и ввод основных регистрационных сведений. Необходимо выбрать учетную запись Майкрософт или рабочую либо школьную учетную запись, которую вам будет удобнее использовать. Если у вас нет таких учетных записей, можно создать учетную запись Майкрософт бесплатно. См. раздел [Регистрация учетной записи Майкрософт](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

Затем выберите параметры пользовательского интерфейса и цветовую тему, которые должны использоваться в Visual Studio. Visual Studio запоминает эти параметры и синхронизирует их во всех средах Visual Studio, в которых вы выполняли вход. Список синхронизируемых параметров см. в разделе [Синхронизированные параметры](../ide/synchronized-settings-in-visual-studio.md). Параметры можно изменить позже в меню **Сервис** > **Параметры** Visual Studio.

После задания параметров будет запущена среда Visual Studio, чтобы можно было начать работу; при этом будет выполнен вход в систему. Чтобы проверить, выполнен ли вход, найдите свое имя в правом верхнем углу среды Visual Studio.

![Текущий пользователь, вошедший в систему VS2017](../ide/media/vs2017_username.png)

Если не выходить из системы, вы будете автоматически входить в Visual Studio при запуске среды. Также будут автоматически применены все изменения синхронизированных параметров. Чтобы выйти из системы, нажмите кнопку со стрелкой вниз рядом с именем профиля в правом верхнем углу среды Visual Studio, выберите команду **Параметры учетной записи**, а затем ссылку **Выход**. Чтобы снова войти в систему, выберите команду **Вход** в правом верхнем углу среды Visual Studio.

## <a name="to-change-your-profile-information"></a>Изменение данных профиля

1. Выберите **Файл** > **Параметры учетной записи** и щелкните ссылку **Управление профилем Visual Studio**.

1. В окне браузера щелкните **Изменить профиль** и измените нужные параметры.

1. После завершения операции выберите **Сохранить изменения**.

## <a name="troubleshooting"></a>Устранение неполадок

Если у вас возникли проблемы при входе, ознакомьтесь со справкой на странице [поддержки учетных записей](https://visualstudio.microsoft.com/subscriptions/support/).

## <a name="see-also"></a>См. также

* [Разблокирование Visual Studio](../ide/how-to-unlock-visual-studio.md)
* [Обзор интегрированной среды разработки Visual Studio](../get-started/visual-studio-ide.md)
* [Вход в систему (Visual Studio для Mac)](/visualstudio/mac/signing-in)
* [Активация (Visual Studio для Mac)](/visualstudio/mac/activation)
