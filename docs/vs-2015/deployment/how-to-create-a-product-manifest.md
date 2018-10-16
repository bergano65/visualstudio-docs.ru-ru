---
title: 'Практическое: создание манифеста продукта | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
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
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: fc5662763e7932cc024169969801c9c321343e32
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270092"
---
# <a name="how-to-create-a-product-manifest"></a>Практическое руководство. Создание манифеста продукта
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы развернуть необходимые условия для приложения, можно создать пакет начального загрузчика. Пакет начального загрузчика содержит один файл манифеста продукта манифест пакета для каждого языкового стандарта. Манифест пакета содержит локализованные компоненты пакета. Сюда входят строки, условия лицензии и языковые пакеты.  
  
 Дополнительные сведения о манифестах продуктов, см. в разделе [как: Create a Package Manifest](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="creating-the-product-manifest"></a>Создание манифеста продукта  
  
#### <a name="to-create-the-product-manifest"></a>Создание манифеста продукта  
  
1.  Создайте каталог для пакета начального загрузчика. В этом примере используется C:\package.  
  
2.  В Visual Studio создайте новый файл XML с именем `product.xml`и сохраните его в папку C:\package.  
  
3.  Добавьте следующий код XML для описания XML-код пространства имен и продукта для пакета. Замените код продукта с уникальным идентификатором для пакета.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Добавьте XML-код, чтобы указать, что пакет имеет зависимость. В этом примере используется зависимость на Microsoft Windows Installer 3.1.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Добавьте XML-код, чтобы получить список всех файлов, находящихся в пакет начального загрузчика. В этом примере используется имя файла пакета CorePackage.msi.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Скопируйте или переместите файл CorePackage.msi C:\package папку.  
  
7.  Добавьте XML-код, чтобы установить пакет с помощью команд загрузчика. Загрузчик автоматически добавляет **/qn** флаг MSI-файл, который будет установки в автоматическом режиме. Если файл является файлом .exe, загрузчик запускает файл .exe с помощью оболочки. Следующий код XML показывает без аргументов для CorePackage.msi, но вы можете поместить аргумент командной строки в атрибуте Arguments.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Добавьте следующий XML-код, проверьте, установлены ли этот пакет начального загрузчика. Замените код продукта с идентификатором GUID для распространяемого компонента.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Добавьте XML-код, чтобы изменить поведение загрузчика в зависимости от того, если уже установлен компонент загрузчика. Если компонент установлен, пакет начального загрузчика не выполняется. Следующий XML-код проверяет, является ли текущий пользователь администратором, так как этот компонент требует полномочий администратора.  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. Добавьте XML-код для задания кодов выхода, если установка прошла успешно, и если необходима перезагрузка. Следующий код XML показано, как завершится неудачей и FailReboot выйти из кодов, которые указывают, что загрузчик не продолжит установку пакетов.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Добавьте следующий XML-код, чтобы завершить раздел команд загрузчика.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Переместите папку C:\package в каталог начального загрузчика Visual Studio. Для Visual Studio 2010 это каталог SDKs\Windows\v7.0A\Bootstrapper\Packages \Program Files\Microsoft.  
  
## <a name="example"></a>Пример  
 Манифест продукта содержит инструкции по установке для пользовательских предварительные требования.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)



