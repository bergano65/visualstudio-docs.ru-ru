---
title: "Пошаговое руководство. Создание пользовательского установщика для приложения ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "развертывание ClickOnce, пользовательский установщик"
  - "пользовательский установщик [ClickOnce]"
  - "развертывание приложений [ClickOnce], пользовательский установщик"
  - "InPlaceHostingManager [ClickOnce], пользовательский установщик"
  - "установщик [ClickOnce], пользовательский"
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 34
---
# Пошаговое руководство. Создание пользовательского установщика для приложения ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Любое приложение ClickOnce на основе EXE\-файла можно автоматически установить и обновить с помощью настраиваемого установщика.  Настраиваемый установщик может реализовать особый пользовательский интерфейс при установке, в том числе специальные диалоговые окна для обслуживания и обеспечения безопасности.  Для выполнения действий установки в настраиваемом установщике используется класс <xref:System.Deployment.Application.InPlaceHostingManager>.  В этом руководстве показан процесс создания настраиваемого установщика, который автоматически устанавливает приложение ClickOnce.  
  
## Обязательные компоненты  
  
### Создание настраиваемого установщика приложения ClickOnce  
  
1.  Добавьте ссылки на элементы System.Deployment и System.Windows.Forms в приложение ClickOnce.  
  
2.  Добавьте в приложение новый класс и укажите для него любое имя.  В этом руководстве используется имя `MyInstaller`.  
  
3.  Добавьте следующие операторы `Imports` или `using` в начало нового класса.  
  
    ```vb#  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```c#  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Добавьте в класс следующие методы.  
  
     Эти методы вызывают методы <xref:System.Deployment.Application.InPlaceHostingManager> для загрузки манифеста развертывания, обеспечения соответствующих разрешений, запроса у пользователя разрешения на установку, а также для последующей загрузки и установки приложения в кэш ClickOnce.  Настраиваемый установщик может заранее описать приложение ClickOnce как доверенное или отложить принятие решения о доверии до вызова метода <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>.  В этом коде приложение заранее описывается как доверенное.  
  
    > [!NOTE]
    >  Разрешения, предоставленные в ходе предоставления предварительного доверия, не могут превышать разрешения кода настраиваемого установщика.  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-cs[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  Чтобы выполнить попытку установки из кода, вызовите метод `InstallApplication`.  Например, если класс назван `MyInstaller`, то элемент `InstallApplication` вызывается следующим образом.  
  
    ```vb#  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```c#  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
  
    ```  
  
## Следующие действия  
 Приложение ClickOnce также может содержать настраиваемую логику обновления, в том числе особый пользовательский интерфейс, отображаемый в ходе обновления.  Дополнительные сведения см. в разделе <xref:System.Deployment.Application.UpdateCheckInfo>.  Приложение ClickOnce также может запрещать создание стандартной записи меню "Пуск", ярлыка и записи в окне "Добавление или удаление программ" с помощью элемента `<customUX>`.  Дополнительные сведения см. в разделах [Элемент \<entryPoint\>](../deployment/entrypoint-element-clickonce-application.md) и <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## См. также  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Элемент \<entryPoint\>](../deployment/entrypoint-element-clickonce-application.md)