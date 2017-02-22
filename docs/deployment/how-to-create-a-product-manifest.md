---
title: "Практическое руководство. Создание манифеста продукта | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "зависимости, пакет пользовательского загрузчика"
  - "необходимые компоненты, пакет пользовательского загрузчика"
  - "файлы продукта [ClickOnce]"
  - "файлы продукта [установщик Windows]"
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Практическое руководство. Создание манифеста продукта
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Чтобы развернуть компоненты, требуемые для работы приложения, можно создать пакет загрузчика.  Пакет загрузчика содержит один файл манифеста продукта для каждого языкового стандарта.  В состав манифеста пакета входят локализованные компоненты пакета.  К ним относятся строки, условия лицензии и языковые пакеты.  
  
 Дополнительные сведения о манифестах продуктов см. в разделе [Практическое руководство. Создание манифеста пакета](../deployment/how-to-create-a-package-manifest.md).  
  
## Создание манифеста продукта  
  
#### Процедура создания манифеста продукта  
  
1.  Создайте каталог для пакета загрузчика.  В данном примере используется каталог "C:\\package".  
  
2.  В Visual Studio создайте новый XML\-файл `product.xml` и сохраните его в папке "C:\\package".  
  
3.  Чтобы описать пространство имен XML и код продукта для пакета, добавьте следующий XML\-код.  Вместо кода продукта укажите уникальный идентификатор пакета.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Чтобы указать, что пакет имеет зависимость, добавьте следующий XML\-код.  В этом примере кода показана зависимость от установщика Microsoft Windows 3.1.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Чтобы указать файлы, содержащиеся в пакете загрузчика, добавьте следующий XML\-код.  В этом примере в качестве имени файла пакета используется CorePackage.msi.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Скопируйте или переместите файл CorePackage.msi в папку "C:\\package".  
  
7.  Чтобы установить пакет с помощью команд загрузчика, добавьте следующий XML\-код.  Загрузчик автоматически добавляет флаг **\/qn** в MSI\-файл, который будет установлен в автоматическом режиме.  Если файл является исполняемым \(EXE\-файл\), загрузчик запускает его с помощью оболочки.  В следующем примере XML\-кода для файла CorePackage.msi не заданы аргументы, однако в атрибут Arguments можно добавить аргумент командной строки.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Чтобы проверить, установлен ли пакет загрузчика, добавьте следующий XML\-код.  Вместо кода продукта укажите GUID распространяемого компонента.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Чтобы изменить поведение загрузчика в зависимости от того, установлен ли компонент загрузчика, добавьте следующий XML\-код.  Если компонент установлен, пакет загрузчика не запустится.  В следующем примере XML\-кода выполняется проверка, является ли текущий пользователь администратором, поскольку для работы этого компонента требуются права администратора.  
  
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
  
10. Чтобы добавить коды выхода при успешной установке и при необходимости перезагрузки, добавьте следующий XML\-код.  В этом примере XML\-кода показаны коды выхода Fail и FailReboot, которые указывают, что загрузчик не будет продолжать установку пакетов.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Чтобы завершить раздел команд загрузчика добавьте следующий XML\-код.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Переместите папку "C:\\package" в каталог загрузчика Visual Studio.  Каталог загрузчика в Visual Studio 2010: \\Program Files\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages.  
  
## Пример  
 Манифест продукта содержит инструкции по установке необходимых компонентов при выборочной установке.  
  
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
  
## См. также  
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)