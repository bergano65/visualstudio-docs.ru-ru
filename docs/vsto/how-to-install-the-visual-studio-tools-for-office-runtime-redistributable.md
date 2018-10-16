---
title: 'Практическое: Установка средств Visual Studio для распространяемого пакета среды выполнения Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 15e3c1b25d4834808fb17e596fcc7babe7dd969f
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255854"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Практическое: Установка средств Visual Studio для распространяемого пакета среды выполнения Office
  Необходимо установить на каждом компьютере, где решений, созданных с помощью средств разработчика Microsoft Office в Visual Studio 2010 Tools для Office runtime [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Она устанавливается автоматически при установке [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и Microsoft Office. Дополнительные сведения см. в разделе [Visual Studio Tools for сценарии установки среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 В указанных ниже ситуациях следуйте описанных инструкциям по установке вручную.  
  
-   Установите на сервер [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Допустим, вы хотите использовать класс <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>, чтобы управлять на сервере решениями на уровне документов.  
  
-   Установите среду выполнения на компьютер, где уже установлены все остальные компоненты, необходимые для решений Office.  
  
    > [!NOTE]  
    >  Для установки .NET Framework и [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] на компьютер разработчика требуются права администратора.  
  
## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Установка среды выполнения Visual Studio Tools для Office  
  
1.  Установите [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии.  
  
    -   Чтобы скачать [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], см. в разделе [Microsoft .NET Framework 4 (веб-установщик)](http://go.microsoft.com/fwlink/?LinkId=178957).  
  
    -   Чтобы скачать [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], см. в разделе [клиентский профиль Microsoft .NET Framework 4 (веб-установщик)](http://go.microsoft.com/fwlink/?LinkId=178958).  
  
    -   Чтобы скачать [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], см. в разделе [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).  
  
2.  Запустите *vstor_redist.exe* для установки [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
     Можно загрузить файлы программы установки из [Visual Studio 2010 Tools для Office runtime](http://go.microsoft.com/fwlink/?LinkId=140384). Предварительные требования [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] совпадают с предварительными требованиями платформы .NET Framework.  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Включает языковые пакеты. Если при установке Windows был выбран не английский язык, сообщения среды выполнения будут отображаться на языке, выбранном для Windows. Точно так же, если конечные пользователи установят [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] и запустят ваши решения в системах Windows, настроенных не на английский язык, сообщения среды выполнения будут отображаться на языке Windows. В некоторых случаях могут потребоваться дополнительные языковые пакеты. Например, может потребоваться дополнительные языковые пакеты, если копия Windows использует более одного параметра языка или переключение на другой язык после вы уже установили [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Вы найдете языковых пакетов на [Microsoft Visual Studio 2010 Tools для языкового пакета Microsoft Office system (среда выполнения версии 4.0)](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>См. также  
 [Начало работы &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Настройка компьютера для разработки решений Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [Практическое: Настройка компьютера для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Практическое: Office установка основных сборок взаимодействия](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)  
  
  