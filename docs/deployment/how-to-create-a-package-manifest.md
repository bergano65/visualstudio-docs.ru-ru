---
title: 'Как: создание манифеста пакета | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 54c2e6a231ce597e2ec6a3e04cf74521b6c10d2e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-a-package-manifest"></a>Практическое руководство. Создание манифеста пакета
Для развертывания необходимых компонентов для приложения, можно использовать пакет начального загрузчика. Пакет начального загрузчика содержит один файл манифеста продукта манифест пакета для каждого языкового стандарта. Общие функциональные возможности для различных локализованных версий должны быть помещены в манифест продукта.  
  
 Дополнительные сведения о манифестах пакетов см. в разделе [как: создание манифеста продукта](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Создание манифеста пакета  
  
#### <a name="to-create-the-package-manifest"></a>Создание манифеста пакета  
  
1.  Создайте каталог для пакета начального загрузчика. В этом примере используется C:\package.  
  
2.  Создайте подкаталог с именем языкового стандарта, например en для английского языка.  
  
3.  В Visual Studio, создайте XML-файл с именем `package.xml`и сохраните его в папку C:\package\en.  
  
4.  Добавьте XML-код для перечисления имя пакета начального загрузчика, язык и региональные параметры для этого локализованного манифеста пакета, а также необязательный лицензионное соглашение. Следующий XML использует переменные `DisplayName` и `Culture`, которые будут описаны далее.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Добавьте XML-код, чтобы вывести список всех файлов, которые находятся в каталоге определенного языкового стандарта. Следующий XML использует файл, который EULA.txt, который применяется для **en** языкового стандарта.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Добавьте XML-код для определения локализуемые строки для пакета начального загрузчика. Следующий XML-код добавляет строки сообщений об ошибках для языкового стандарта en.  
  
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
 Манифест пакета содержит языкового стандарта, например сообщения об ошибках, условия лицензионного соглашения и языковые пакеты.  
  
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