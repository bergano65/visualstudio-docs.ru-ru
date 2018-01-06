---
title: "Пошаговое руководство: Создание пользовательского установщика для приложения ClickOnce | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "34"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 06c048db48173913a2e1102d1e70f07369316439
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>Пошаговое руководство. Создание пользовательского установщика для приложения ClickOnce
Любое приложение ClickOnce на основе файла .exe можно автоматически устанавливается и обновляется с помощью настраиваемого установщика. Пользовательский установщик может реализовать особый пользовательский интерфейс во время установки, включая пользовательские диалоговые окна для обслуживания и обеспечения безопасности. Для выполнения операции по установке, использует пользовательский установщик <xref:System.Deployment.Application.InPlaceHostingManager> класса. В этом пошаговом руководстве показано, как создать пользовательский установщик, который автоматически устанавливает приложение ClickOnce.  
  
## <a name="prerequisites"></a>Предварительные требования  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>Для создания настраиваемого установщика приложения ClickOnce  
  
1.  В приложении ClickOnce и добавьте ссылки на System.Deployment и System.Windows.Forms.  
  
2.  Добавьте новый класс в приложение и укажите любое имя. В этом пошаговом руководстве используется имя `MyInstaller`.  
  
3.  Добавьте следующие `Imports` или `using` в начале нового класса.  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Добавьте следующие методы в класс.  
  
     Эти методы вызывают <xref:System.Deployment.Application.InPlaceHostingManager> способы загрузки манифеста развертывания, обеспечения соответствующих разрешений, запрашивать у пользователя разрешения для установки, затем загрузите и установите приложения в кэше ClickOnce. Можно указать пользовательский установщик предварительно доверенного приложения ClickOnce или можно отложить решение о доверии <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> вызова метода. Этот код предварительно отношение доверия приложения.  
  
    > [!NOTE]
    >  Разрешения, назначенные, предварительно доверять не может превышать разрешения кода настраиваемого установщика.  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  Чтобы выполнить попытку установки из кода, вызовите `InstallApplication` метод. Например, если класс назван `MyInstaller`, можно вызвать метод `InstallApplication` следующим образом.  
  
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
 Приложения ClickOnce, также можно добавить настраиваемую логику обновления, включая пользовательский интерфейс для отображения во время процесса обновления. Дополнительные сведения см. в разделе <xref:System.Deployment.Application.UpdateCheckInfo>. ClickOnce-приложения также можно подавлять стандартной записи меню "Пуск", ярлык и добавление или удаление программ с помощью `<customUX>` элемента. Дополнительные сведения см. в разделе [ \<entryPoint > элемент](../deployment/entrypoint-element-clickonce-application.md) и <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## <a name="see-also"></a>См. также  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint > элемент](../deployment/entrypoint-element-clickonce-application.md)