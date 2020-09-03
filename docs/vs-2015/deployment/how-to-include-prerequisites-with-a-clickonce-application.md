---
title: Как включить необходимые компоненты в приложение ClickOnce | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9639da1f735095f6d04a59d1f2302f822423e006
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "77557673"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Практическое руководство. Включение требуемых компонентов в дистрибутив приложения ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Перед распространением программного обеспечения необходимых компонентов с приложением [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] следует загрузить на компьютер разработчика пакеты установщиков этих необходимых компонентов. При публикации приложения и выборе **загрузки необходимых компонентов из того же расположения, что и мое приложение**, произойдет ошибка, если пакеты установщика отсутствуют в папке **packages** .  
  
> [!NOTE]
> Чтобы добавить пакет установщика для .NET Framework, ознакомьтесь с [руководством по развертыванию .NET Framework для разработчиков](/dotnet/framework/deployment/deployment-guide-for-developers).  
  
## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> Добавление пакета установщика с помощью файла Package.xml  
  
1. В проводнике откройте папку **Packages**.  
  
     Путь по умолчанию: C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages (для 32-разрядной системы) и C:\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages (для 64-разрядной системы).  
  
2. Откройте папку необходимого компонента, который требуется добавить, а затем папку языка для установленной версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (например, **ru** для русского языка).  
  
3. В блокноте откройте файл **Package.xml**.  
  
4. Выберите элемент **Name** , содержащий `http://go.microsoft.com/fwlink` , и скопируйте URL-адрес. Включите часть **LinkID**.  
  
    > [!NOTE]
    > Если элемент **Name** не содержит `http://go.microsoft.com/fwlink` , откройте файл **Product.xml** в корневой папке для необходимого компонента и перейдите к строке **fwlink** .  
  
    > [!IMPORTANT]
    > Некоторые необходимые компоненты имеют несколько пакетов установщиков (например, для 32-разрядных или 64-разрядных систем). Если строка **fwlink** содержится в нескольких элементах **Имя**, оставшиеся действия следует выполнить для каждого из них.  
  
5. Вставьте URL-адрес в адресную строку браузера, а затем, при получении запроса на выполнение или сохранение, нажмите кнопку **Сохранить**.  
  
     На этом шаге файл установщика загружается на компьютер.  
  
6. Скопируйте файл в корневую папку необходимого компонента.  
  
     Например, для необходимого компонента "Установщик Windows 4.5" скопируйте файл в папку \Packages\WindowsInstaller4_5.  
  
     Теперь можно распространить пакет установщика с приложением.  
  
## <a name="see-also"></a>См. также:  
 [Практическое руководство. Установка необходимых компонентов при помощи ClickOnce-приложения](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
