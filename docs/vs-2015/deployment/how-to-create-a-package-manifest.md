---
title: Как создать манифест пакета | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c711c50ab484cc88b1d6aff5c8e3018cead69953
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153838"
---
# <a name="how-to-create-a-package-manifest"></a>Практическое руководство. Создание манифеста пакета
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы развернуть необходимые компоненты для приложения, можно использовать пакет начального загрузчика. Пакет загрузчика содержит один файл манифеста продукта, но манифест пакета для каждого языкового стандарта. Общие функции в разных локализованных версиях должны поступать в манифест продукта.  
  
 Дополнительные сведения о манифестах пакетов см. [в разделе инструкции. Создание манифеста продукта](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Создание манифеста пакета  
  
#### <a name="to-create-the-package-manifest"></a>Создание манифеста пакета  
  
1. Создайте каталог для пакета начального загрузчика. В этом примере используется К:\паккаже.  
  
2. Создайте подкаталог с именем локали, например en для английского языка.  
  
3. В Visual Studio создайте XML-файл с именем `package.xml` и сохраните его в папку к:\паккаже\ен.  
  
4. Добавьте XML, чтобы вывести имя пакета начального загрузчика, язык и региональные параметры для манифеста локализованного пакета, а также необязательное лицензионное соглашение. В следующем коде XML используются переменные `DisplayName` и `Culture` , которые определены в более позднем элементе.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5. Добавьте XML-код, чтобы вывести список всех файлов, которые находятся в каталоге для конкретного языкового стандарта. В следующем XML-коде используется файл с именем eula.txt, который применим для языка **EN** .  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6. Добавьте XML, чтобы определить локализуемые строки для пакета начального загрузчика. Следующий код XML добавляет строки ошибок для языкового стандарта EN.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7. Скопируйте папку К:\паккаже в каталог начального загрузчика Visual Studio. Для Visual Studio 2010 это каталог \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
## <a name="example"></a>Пример  
 Манифест пакета содержит сведения, относящиеся к языковому стандарту, такие как сообщения об ошибках, условия лицензии на программное обеспечение и языковые пакеты.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)
