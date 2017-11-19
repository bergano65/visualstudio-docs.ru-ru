---
title: "Как: Установка набора средств Visual Studio для распространяемого пакета среды выполнения Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
ms.assetid: ac7a9ad3-e810-4d7f-a0e2-9992c9036b8d
caps.latest.revision: "94"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8d3439a98a445761a8d357d9b4bef631da034943
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Практическое руководство. Установка распространяемого пакета среды выполнения набора средств Visual Studio для Office
  Средства Visual Studio 2010 для среды выполнения Office должны устанавливаться на каждом компьютере, где решений, созданных с помощью средств разработчика Microsoft Office в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Она устанавливается автоматически при установке [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и Microsoft Office. Для получения дополнительной информации см. [Visual Studio Tools for Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 В указанных ниже ситуациях следуйте описанных инструкциям по установке вручную.  
  
-   Установите на сервер [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Допустим, вы хотите использовать класс <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>, чтобы управлять на сервере решениями на уровне документов.  
  
-   Установите среду выполнения на компьютер, где уже установлены все остальные компоненты, необходимые для решений Office.  
  
    > [!NOTE]  
    >  Для установки .NET Framework и [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] на компьютер разработчика требуются права администратора.  
  
### <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Установка среды выполнения Visual Studio Tools для Office  
  
1.  Установите [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии.  
  
    -   Чтобы загрузить [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], в разделе [Microsoft .NET Framework 4 (веб-установщик)](http://go.microsoft.com/fwlink/?LinkId=178957).  
  
    -   Чтобы загрузить [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], в разделе [профиль клиента Microsoft .NET Framework 4 (веб-установщик)](http://go.microsoft.com/fwlink/?LinkId=178958).  
  
    -   Чтобы загрузить [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], в разделе [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).  
  
2.  Запустите файл vstor_redist.exe для установки [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
     Можно загрузить эти файлы программы установки из [Visual Studio 2010 Tools для Office Runtime](http://go.microsoft.com/fwlink/?LinkId=140384). Предварительные требования [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] совпадают с предварительными требованиями платформы .NET Framework.  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Включает языковые пакеты. Если при установке Windows был выбран не английский язык, сообщения среды выполнения будут отображаться на языке, выбранном для Windows. Точно так же, если конечные пользователи установят [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] и запустят ваши решения в системах Windows, настроенных не на английский язык, сообщения среды выполнения будут отображаться на языке Windows. В некоторых случаях могут потребоваться дополнительные языковые пакеты. Например, могут потребоваться дополнительные языковые пакеты Если копии Windows используется более одного параметра языка или переключение на другой язык после установки [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Можно найти языковых пакетов на [Microsoft Visual Studio 2010 Tools для системы Microsoft Office (среда выполнения версии 4.0) языковой пакет](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>См. также  
 [Приступая к работе &#40; разработка решений Office в Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [Как: Настройка компьютера для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Как: Установка основных сборок взаимодействия Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)  
  
  