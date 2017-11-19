---
title: "Как: включить необходимые компоненты ClickOnce-приложения | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 18431ea15b53959234da4b2c6dedb24b8fa2e390
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Практическое руководство. Включение требуемых компонентов в дистрибутив приложения ClickOnce
Перед распространением программного обеспечения необходимых компонентов с приложением [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] следует загрузить на компьютер разработчика пакеты установщиков этих необходимых компонентов. После публикации приложения и нажатия кнопки **загрузить необходимые компоненты с местоположения моего приложения**, произойдет ошибка, если пакеты установщиков отсутствуют в **пакетов** папки.  
  
> [!NOTE]
>  Чтобы добавить пакет установщика для платформы .NET Framework, см. [руководство по развертыванию .NET Framework для разработчиков](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
##  <a name="Package"></a>Добавление пакета установщика с помощью файла Package.xml  
  
1.  В проводнике откройте **пакетов** папки.  
  
     Путь по умолчанию: C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages (для 32-разрядной системы) и C:\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages (для 64-разрядной системы).  
  
2.  Откройте папку необходимого компонента, который требуется добавить, а затем откройте папку языка для установленной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (например, **en** для английского языка).  
  
3.  В блокноте откройте **Package.xml** файла.  
  
4.  Найдите **имя** элемент, содержащий **http://go.microsoft.com/fwlink**и скопируйте URL-адрес. Включить **LinkID** часть.  
  
    > [!NOTE]
    >  Если не **имя** элемент содержит **http://go.microsoft.com/fwlink**откройте **Product.xml** в корневой папке необходимого компонента и найдите  **fwlink** строка.  
  
    > [!IMPORTANT]
    >  Некоторые необходимые компоненты имеют несколько пакетов установщиков (например, для 32-разрядных или 64-разрядных систем). При наличии нескольких **имя** элементы содержат **fwlink**, остальные действия необходимо повторить для каждого из них.  
  
5.  Вставьте URL-адрес в адресную строку браузера, а затем выберите при появлении запроса на выполнение или сохранение **Сохранить**.  
  
     На этом шаге файл установщика загружается на компьютер.  
  
6.  Скопируйте файл в корневую папку необходимого компонента.  
  
     Например, для необходимого компонента "Установщик Windows 4.5" скопируйте файл в папку \Packages\WindowsInstaller4_5.  
  
     Теперь можно распространить пакет установщика с приложением.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Установка необходимых компонентов для приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)