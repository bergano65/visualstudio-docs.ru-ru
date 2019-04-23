---
title: Пошаговое руководство. Создание пользовательского установщика для приложения ClickOnce | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 635dd8d9f7860b075de9b35e21fcf42bdad2ea1a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078881"
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>Пошаговое руководство. Создание пользовательского установщика для приложения ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Любое приложение, на основе файла .exe можно автоматически устанавливается и обновляется с помощью настраиваемого установщика. Пользовательский установщик можно реализовать настраиваемый пользовательский интерфейс во время установки, включая пользовательские диалоговые окна для обслуживания и обеспечения безопасности. Для выполнения операции установки, использует пользовательский установщик <xref:System.Deployment.Application.InPlaceHostingManager> класса. В этом пошаговом руководстве показано, как создать пользовательский установщик, который автоматически устанавливает приложения ClickOnce.  
  
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
    >  Разрешения, назначенные, предварительно доверять не может превышать разрешения кода пользовательского установщика.  
  
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs#1)]
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb#1)]  
  
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
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Элемент \<entryPoint>](../deployment/entrypoint-element-clickonce-application.md)
