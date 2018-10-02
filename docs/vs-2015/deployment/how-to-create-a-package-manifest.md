---
title: 'Практическое: создание манифеста пакета | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 6abbbb351d04251b4ef1c209f35652a91b11d8c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569931"
---
# <a name="how-to-create-a-package-manifest"></a>Практическое руководство. Создание манифеста пакета
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Create a Package Manifest](https://docs.microsoft.com/visualstudio/deployment/how-to-create-a-package-manifest).  
  
Чтобы развернуть необходимые условия для приложения, можно использовать пакет начального загрузчика. Пакет начального загрузчика содержит один файл манифеста продукта манифест пакета для каждого языкового стандарта. Общие функции для различных локализованных версий следует перейти в манифест продукта.  
  
 Дополнительные сведения о манифестах пакетов см. в разделе [как: Create a Product Manifest](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Создание манифеста пакета  
  
#### <a name="to-create-the-package-manifest"></a>Создание манифеста пакета  
  
1.  Создайте каталог для пакета начального загрузчика. В этом примере используется C:\package.  
  
2.  Создайте подкаталог с именем языкового стандарта, например en для английского языка.  
  
3.  В Visual Studio создайте XML-файл с именем `package.xml`и сохраните его в папку C:\package\en.  
  
4.  Добавьте XML-код, чтобы получить список имя пакета начального загрузчика, язык и региональные параметры для этого локализованного манифеста пакета и необязательный лицензионного соглашения. Следующий код XML использует переменные `DisplayName` и `Culture`, которые определены в элементе более поздней версии.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Добавьте XML-код, чтобы получить список всех файлов, которые находятся в каталоге, зависящих от языкового стандарта. Следующий код XML использует файл с именем eula.txt, предназначенный для **en** языкового стандарта.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Добавьте XML-код, чтобы определить локализуемые строки для пакета начального загрузчика. Следующий XML-код добавляет строки сообщений об ошибках для языкового стандарта en.  
  
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
  
7.  Скопируйте папку C:\package в каталог начального загрузчика Visual Studio. Для Visual Studio 2010 это каталог SDKs\Windows\v7.0A\Bootstrapper\Packages \Program Files\Microsoft.  
  
## <a name="example"></a>Пример  
 Манифест пакета содержит зависящие от языкового стандарта, например сообщения об ошибках, условия лицензии и языковые пакеты.  
  
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
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)



