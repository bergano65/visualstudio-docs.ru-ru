---
title: "Практическое руководство. Установка распространяемого пакета среды выполнения Visual Studio Tools for Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "установка средств разработки Office в Visual Studio"
  - "Office - среда выполнения [разработка решений Office в Visual Studio]"
ms.assetid: ac7a9ad3-e810-4d7f-a0e2-9992c9036b8d
caps.latest.revision: 94
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 93
---
# Практическое руководство. Установка распространяемого пакета среды выполнения Visual Studio Tools for Office
  На каждом компьютере должна быть установлена среда выполнения Visual Studio 2010 Tools для Office, которая запускает решения, создаваемые с помощью средств разработчика Microsoft Office в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Она устанавливается автоматически при установке [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и Microsoft Office.  Дополнительные сведения см. в разделе [Сценарии установки среды выполнения Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 В указанных ниже ситуациях следуйте описанных инструкциям по установке вручную.  
  
-   Установите на сервер [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  Допустим, вы хотите использовать класс <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>, чтобы управлять на сервере решениями на уровне документов.  
  
-   Установите среду выполнения на компьютер, где уже установлены все остальные компоненты, необходимые для решений Office.  
  
    > [!NOTE]  
    >  Для установки .NET Framework и [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] на компьютер разработчика требуются права администратора.  
  
### Установка среды выполнения Visual Studio Tools для Office  
  
1.  Установите [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии.  
  
    -   Загрузить [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] можно на странице [Microsoft .NET Framework 4 \(веб\-установщик\)](http://go.microsoft.com/fwlink/?LinkId=178957).  
  
    -   Загрузить [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] можно на странице [Клиентский профиль Microsoft .NET Framework 4 \(веб\-установщик\)](http://go.microsoft.com/fwlink/?LinkId=178958).  
  
    -   Загрузить [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] можно на странице [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).  
  
2.  Запустите файл vstor\_redist.exe для установки [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
     Загрузить файлы программы установки можно на странице [Инструменты Visual Studio 2010 для среды выполнения Office](http://go.microsoft.com/fwlink/?LinkId=140384).  Предварительные требования [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] совпадают с предварительными требованиями платформы .NET Framework.  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] включает языковые пакеты.  Если при установке Windows был выбран не английский язык, сообщения среды выполнения будут отображаться на языке, выбранном для Windows.  Точно так же, если конечные пользователи установят [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] и запустят ваши решения в системах Windows, настроенных не на английский язык, сообщения среды выполнения будут отображаться на языке Windows.  В некоторых случаях могут потребоваться дополнительные языковые пакеты.  Например, дополнительные языковые пакеты могут потребоваться, если в копии Windows используется больше одного языка либо после установки [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] система переключается на другой язык.  Языковые пакеты можно найти на странице [Языковой пакет для набора средств Microsoft Visual Studio 2010 для системы Office \(среда выполнения версии 4.0\)](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## См. также  
 [Начало работы &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Настройка компьютера для разработки решений Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [Практическое руководство. Настройка компьютера для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Практическое руководство. Установка основных сборок взаимодействия Microsoft Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)  
  
  