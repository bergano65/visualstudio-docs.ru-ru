---
title: Создание манифеста продукта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: how-to
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0f4302756b089376eca8926453399768faaf58f
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382514"
---
# <a name="how-to-create-a-product-manifest"></a>Практическое руководство. Создание манифеста продукта
Чтобы развернуть необходимые компоненты для приложения, можно создать пакет начального загрузчика. Пакет загрузчика содержит один файл манифеста продукта, но манифест пакета для каждого языкового стандарта. Манифест пакета содержит особенности локализации пакета. Сюда входят строки, лицензионные соглашения для конечных пользователей и языковые пакеты.

 Дополнительные сведения о манифестах пакетов см. [в разделе инструкции. Создание манифеста пакета](../deployment/how-to-create-a-package-manifest.md).

## <a name="create-the-product-manifest"></a>Создание манифеста продукта

#### <a name="to-create-the-product-manifest"></a>Создание манифеста продукта

1. Создайте каталог для пакета начального загрузчика. В этом примере используется К:\паккаже.

2. В Visual Studio создайте новый XML-файл с именем *product.xml*и сохраните его в папку *к:\паккаже* .

3. Добавьте следующий XML-код для описания пространства имен XML и кода продукта для пакета. Замените код продукта уникальным идентификатором пакета.

    ```xml
    <Product
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
    ProductCode="Custom.Bootstrapper.Package">
    ```

4. Добавьте XML, чтобы указать, что пакет имеет зависимость. В этом примере используется зависимость от Microsoft установщик Windows 3,1.

    ```xml
    <RelatedProducts>
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
      </RelatedProducts>
    ```

5. Добавьте XML-код, чтобы вывести список всех файлов, которые находятся в пакете начального загрузчика. В этом примере используется имя файла пакета *CorePackage.msi*.

    ```xml
    <PackageFiles>
        <PackageFile Name="CorePackage.msi"/>
    </PackageFiles>
    ```

6. Скопируйте или переместите файл *CorePackage.msi* в папку *к:\паккаже* .

7. Добавьте XML для установки пакета с помощью команд начального загрузчика. Загрузчик автоматически добавляет флаг **/qn** в *MSI* файл, который будет устанавливаться в автоматическом режиме. Если файл является *exe*-файлом, загрузчик запускает *exe* -файл с помощью оболочки. В следующем коде XML не отображаются аргументы для *CorePackage.msi*, но в атрибут можно вставить аргумент командной строки `Arguments` .

    ```xml
    <Commands>
        <Command PackageFile="CorePackage.msi" Arguments="">
    ```

8. Добавьте следующий XML-код, чтобы проверить, установлен ли этот пакет загрузчика. Замените код продукта идентификатором GUID распространяемого компонента.

    ```xml
    <InstallChecks>
        <MsiProductCheck
            Property="IsMsiInstalled"
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
    </InstallChecks>
    ```

9. Добавьте XML, чтобы изменить поведение загрузчика в зависимости от того, был ли уже установлен компонент загрузчика. Если компонент установлен, то пакет загрузчика не запускается. Следующий код XML проверяет, является ли текущий пользователь администратором, поскольку этому компоненту требуются права администратора.

    ```xml
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

    ```xml
    <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
    </ExitCodes>
    ```

11. Добавьте следующий XML-код, чтобы завершить раздел для команд начального загрузчика.

    ```xml
        </Command>
    </Commands>
    ```

12. Переместите папку *к:\паккаже* в каталог начального загрузчика Visual Studio. Для Visual Studio 2010 это каталог *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* .

## <a name="example"></a>Пример
 Манифест продукта содержит инструкции по установке для пользовательских компонентов.

```xml
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
- [Справочник по схеме продуктов и пакетов](../deployment/product-and-package-schema-reference.md)