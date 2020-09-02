---
title: Как создать манифест продукта | Документация Майкрософт
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
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73e2c3f2c9736fd762a9e763827ed641ea5069f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153826"
---
# <a name="how-to-create-a-product-manifest"></a>Практическое руководство. Создание манифеста продукта
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы развернуть необходимые компоненты для приложения, можно создать пакет начального загрузчика. Пакет загрузчика содержит один файл манифеста продукта, но манифест пакета для каждого языкового стандарта. Манифест пакета содержит особенности локализации пакета. Сюда входят строки, лицензионные соглашения для конечных пользователей и языковые пакеты.  
  
 Дополнительные сведения о манифестах продуктов см. [в разделе инструкции. Создание манифеста пакета](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="creating-the-product-manifest"></a>Создание манифеста продукта  
  
#### <a name="to-create-the-product-manifest"></a>Создание манифеста продукта  
  
1. Создайте каталог для пакета начального загрузчика. В этом примере используется К:\паккаже.  
  
2. В Visual Studio создайте новый XML-файл с именем `product.xml` и сохраните его в папку к:\паккаже.  
  
3. Добавьте следующий XML-код для описания пространства имен XML и кода продукта для пакета. Замените код продукта уникальным идентификатором пакета.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4. Добавьте XML, чтобы указать, что пакет имеет зависимость. В этом примере используется зависимость от Microsoft установщик Windows 3,1.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5. Добавьте XML-код, чтобы вывести список всех файлов, которые находятся в пакете начального загрузчика. В этом примере используется имя файла пакета CorePackage.msi.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6. Скопируйте или переместите файл CorePackage.msi в папку К:\паккаже.  
  
7. Добавьте XML для установки пакета с помощью команд начального загрузчика. Загрузчик автоматически добавляет флаг **/qn** в MSI файл, который будет устанавливаться в автоматическом режиме. Если файл является EXE-файлом, загрузчик запускает exe-файл с помощью оболочки. Следующий XML-код не показывает никаких аргументов для CorePackage.msi, но аргумент командной строки можно разместить в атрибуте arguments.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8. Добавьте следующий XML-код, чтобы проверить, установлен ли этот пакет загрузчика. Замените код продукта идентификатором GUID распространяемого компонента.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Добавьте XML, чтобы изменить поведение загрузчика в зависимости от того, был ли уже установлен компонент загрузчика. Если компонент установлен, то пакет загрузчика не запускается. Следующий код XML проверяет, является ли текущий пользователь администратором, поскольку этому компоненту требуются права администратора.  
  
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
  
10. Добавьте XML-код, чтобы задать коды выхода, если установка выполнена успешно и требуется перезагрузка. В следующем коде XML показаны коды выхода Fail и Фаилребут, указывающие, что загрузчик не будет продолжать установку пакетов.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Добавьте следующий XML-код, чтобы завершить раздел для команд начального загрузчика.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Переместите папку К:\паккаже в каталог начального загрузчика Visual Studio. Для Visual Studio 2010 это каталог \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
## <a name="example"></a>Пример  
 Манифест продукта содержит инструкции по установке для пользовательских компонентов.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)
