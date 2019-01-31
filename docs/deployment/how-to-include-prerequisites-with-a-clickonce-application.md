---
title: Как выполнить Включить необходимые компоненты ClickOnce-приложения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b83272cedce161ce9122d5877ab4afecca1b3ec
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998512"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Как выполнить включение требуемых компонентов в дистрибутив приложения ClickOnce
Перед распространением программного обеспечения необходимых компонентов с приложением [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] следует загрузить на компьютер разработчика пакеты установщиков этих необходимых компонентов. Если в папке **Packages** пакеты установщиков отсутствуют, при публикации приложения и выборе команды **Загрузить необходимые компоненты с местоположения моего приложения** произойдет ошибка.  
  
> [!NOTE]
>  Чтобы добавить пакет установщика для .NET Framework, см. в разделе [руководство по развертыванию .NET Framework для разработчиков](/dotnet/framework/deployment/deployment-guide-for-developers).  
  
##  <a name="Package"></a> Добавление пакета установщика с помощью файла Package.xml  
  
1. В проводнике откройте папку **Packages**.  
  
    Путь по умолчанию: *C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* (для 32-разрядной системы) и *C:\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* (для 64-разрядной системы).  
  
2. Откройте папку необходимого компонента, который требуется добавить, а затем папку языка для установленной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (например, **ru** для русского языка).  
  
3. В блокноте откройте файл *Package.xml*.  
  
4. Найдите **имя** элемент, содержащий **http://go.microsoft.com/fwlink**и скопируйте URL-адрес. Включите часть **LinkID**.  
  
   > [!NOTE]
   >  Если не **имя** элемент содержит **http://go.microsoft.com/fwlink**откройте **Product.xml** файл в корневой папке необходимого компонента и найдите **fwlink** строка.  
  
   > [!IMPORTANT]
   >  Некоторые необходимые компоненты имеют несколько пакетов установщиков (например, для 32-разрядных или 64-разрядных систем). Если строка **fwlink** содержится в нескольких элементах **Имя**, оставшиеся действия следует выполнить для каждого из них.  
  
5. Вставьте URL-адрес в адресную строку браузера, а затем, при получении запроса на выполнение или сохранение, нажмите кнопку **Сохранить**.  
  
    На этом шаге файл установщика загружается на компьютер.  
  
6. Скопируйте файл в корневую папку необходимого компонента.  
  
    Например, для необходимого компонента "Установщик Windows 4.5" скопируйте файл в папку *\Packages\WindowsInstaller4_5*.  
  
    Теперь можно распространить пакет установщика с приложением.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Установить обязательные компоненты приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)