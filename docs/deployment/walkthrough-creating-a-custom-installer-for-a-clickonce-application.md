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
ms.openlocfilehash: e6969490789b4f5747c28f33e91c7d61e97de52e
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263461"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Пошаговое руководство. Создание пользовательского установщика для приложения ClickOnce
Любое приложение на основе *.exe* автоматически устанавливается и обновляется с помощью настраиваемого установщика файл. Пользовательский установщик можно реализовать настраиваемый пользовательский интерфейс во время установки, включая пользовательские диалоговые окна для обслуживания и обеспечения безопасности. Для выполнения операции установки, использует пользовательский установщик <xref:System.Deployment.Application.InPlaceHostingManager> класса. В этом пошаговом руководстве показано, как создать пользовательский установщик, который автоматически устанавливает приложения ClickOnce.

## <a name="prerequisites"></a>Предварительные требования

### <a name="to-create-a-custom-clickonce-application-installer"></a>Чтобы создать пользовательский установщик приложений ClickOnce

1. В приложении ClickOnce добавьте ссылки на System.Deployment и System.Windows.Forms.

2. Добавьте новый класс в приложение и укажите любое имя. В этом пошаговом руководстве используется имя `MyInstaller`.

3. Добавьте следующий `Imports` или `using` инструкции в начало нового класса.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Добавьте следующие методы в класс.

     Эти методы вызывают <xref:System.Deployment.Application.InPlaceHostingManager> способы загрузки манифеста развертывания, обеспечения соответствующих разрешений, попросите пользователя для разрешения установить, а затем загрузите и установите приложения в кэш ClickOnce. Пользовательский установщик можно указать, что ClickOnce-приложения является предварительно доверенным или отложить решение о доверии <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> вызова метода. Этот код предварительно доверяет приложение.

    > [!NOTE]
    > Разрешения, назначенные, предварительно доверять не может превышать разрешения кода пользовательского установщика.

     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]

5. Попытка установки из кода, вызовите `InstallApplication` метод. Например, если класс назван `MyInstaller`, можно назвать `InstallApplication` следующим образом.

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
 Приложения ClickOnce можно также добавить настраиваемую логику обновления, включая пользовательский интерфейс для отображения во время обновления. Дополнительные сведения см. в разделе <xref:System.Deployment.Application.UpdateCheckInfo>. ClickOnce-приложения также можно отключить стандартные записи меню "Пуск", ярлыка и добавление или удаление программ с помощью `<customUX>` элемент. Дополнительные сведения см. в разделе [ \<entryPoint > элемент](../deployment/entrypoint-element-clickonce-application.md) и <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.

## <a name="see-also"></a>См. также
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<entryPoint > элемент](../deployment/entrypoint-element-clickonce-application.md)