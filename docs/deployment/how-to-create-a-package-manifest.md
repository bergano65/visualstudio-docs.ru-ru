---
title: Создание манифеста пакета | Документация Майкрософт
description: Узнайте об использовании пакета начального загрузчика для развертывания необходимых компонентов для приложения ClickOnce, которое содержит манифест пакета для каждого языкового стандарта.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cef6cd23a1e5ff1e00e2d4d93313ee1e9355ece2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927565"
---
# <a name="how-to-create-a-package-manifest"></a>Практическое руководство. Создание манифеста пакета
Чтобы развернуть необходимые компоненты для приложения, можно использовать пакет начального загрузчика. Пакет загрузчика содержит один файл манифеста продукта, но манифест пакета для каждого языкового стандарта. Общие функции в разных локализованных версиях должны поступать в манифест продукта.

 Дополнительные сведения о манифестах продуктов см. [в разделе инструкции. Создание манифеста продукта](../deployment/how-to-create-a-product-manifest.md).

## <a name="create-the-package-manifest"></a>Создание манифеста пакета

#### <a name="to-create-the-package-manifest"></a>Создание манифеста пакета

1. Создайте каталог для пакета начального загрузчика. В этом примере используется *к:\паккаже*.

2. Создайте подкаталог с именем локали, например *EN* для английского языка.

3. В Visual Studio создайте XML-файл с именем *package.xml* и сохраните его в папку *к:\паккаже\ен* .

4. Добавьте XML, чтобы вывести имя пакета начального загрузчика, язык и региональные параметры для манифеста локализованного пакета, а также необязательное лицензионное соглашение. В следующем коде XML используются переменные `DisplayName` и `Culture` , которые определены в более позднем элементе.

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. Добавьте XML-код, чтобы вывести список всех файлов, которые находятся в каталоге для конкретного языкового стандарта. В следующем XML-коде используется файл с именем *eula.txt* , который применим для языка **EN** .

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. Добавьте XML, чтобы определить локализуемые строки для пакета начального загрузчика. Следующий код XML добавляет строки ошибок для языкового стандарта **EN** .

    ```xml
      <Strings>
        <String Name="DisplayName">Custom Bootstrapper Package</String>
        <String Name="CultureName">en</String>
        <String Name="NotAnAdmin">You must be an administrator to install
    this package.</String>
        <String Name="GeneralFailure">A general error has occurred while
    installing this package.</String>
    </Strings>
    ```

7. Скопируйте папку *к:\паккаже* в каталог начального загрузчика Visual Studio. Для Visual Studio 2010 это каталог *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* .

## <a name="example"></a>Пример
 Манифест пакета содержит сведения, относящиеся к языковому стандарту, такие как сообщения об ошибках, условия лицензии на программное обеспечение и языковые пакеты.

```xml
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

## <a name="see-also"></a>См. также раздел
- [Справочник по схеме продуктов и пакетов](../deployment/product-and-package-schema-reference.md)