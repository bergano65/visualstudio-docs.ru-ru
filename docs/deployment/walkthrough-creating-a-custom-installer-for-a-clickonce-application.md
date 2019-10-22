---
title: Создание пользовательского установщика для приложения ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b648134b7ad27a8f622ce270dc0f05e0a7e6516c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637424"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Пошаговое руководство. Создание пользовательского установщика для приложения ClickOnce
Любое приложение ClickOnce, основанное на *exe* -файле, может устанавливаться автоматически и обновляться с помощью пользовательского установщика. Пользовательский установщик может реализовать пользовательский интерфейс во время установки, включая пользовательские диалоговые окна для операций безопасности и обслуживания. Для выполнения операций установки Настраиваемый установщик использует класс <xref:System.Deployment.Application.InPlaceHostingManager>. В этом пошаговом руководстве показано, как создать пользовательский установщик, который автоматически устанавливает приложение ClickOnce.

## <a name="prerequisites"></a>Необходимые компоненты

### <a name="to-create-a-custom-clickonce-application-installer"></a>Создание пользовательского установщика приложения ClickOnce

1. В приложении ClickOnce добавьте ссылки на System. Deployment и System. Windows. Forms.

2. Добавьте в приложение новый класс и укажите любое имя. В этом пошаговом руководстве используется имя `MyInstaller`.

3. Добавьте следующие директивы `Imports` или `using` в начало нового класса.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Добавьте в класс следующие методы.

     Эти методы вызывают <xref:System.Deployment.Application.InPlaceHostingManager> методы для загрузки манифеста развертывания, утверждения соответствующих разрешений, попросите пользователя установить разрешение на установку, а затем скачайте и установите приложение в кэш ClickOnce. Пользовательский установщик может указать, что приложение ClickOnce является предварительно доверенным, или может отложить принятие решения о доверии вызовом метода <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>. Этот код предварительно доверяет приложению.

    > [!NOTE]
    > Разрешения, назначенные с помощью предварительного доверия, не могут превышать разрешения пользовательского кода установщика.

     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]

5. Чтобы попытаться выполнить установку из кода, вызовите метод `InstallApplication`. Например, если вы назовете класс `MyInstaller`, вы можете вызвать `InstallApplication` следующим образом.

    ```vb
    Dim installer As New MyInstaller()
    installer.InstallApplication("\\myServer\myShare\myApp.application")
    MessageBox.Show("Installer object created.")
    ```

    ```csharp
    MyInstaller installer = new MyInstaller();
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");
    MessageBox.Show("Installer object created.");
    ```

## <a name="next-steps"></a>Следующие шаги
 Приложение ClickOnce может также добавлять пользовательскую логику обновления, включая пользовательский интерфейс, отображаемый во время процесса обновления. Для получения дополнительной информации см. <xref:System.Deployment.Application.UpdateCheckInfo>. Приложение ClickOnce также может подавлять стандартную запись меню "Пуск", ярлык, а также запись "Установка и удаление программ" с помощью элемента `<customUX>`. Дополнительные сведения см. в разделе [\<entryPoint > Element](../deployment/entrypoint-element-clickonce-application.md) и <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.

## <a name="see-also"></a>См. также
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<entryPoint > элемент](../deployment/entrypoint-element-clickonce-application.md)
