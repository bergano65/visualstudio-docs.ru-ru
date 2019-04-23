---
title: Практическое руководство. Создание манифеста продукта | Документация Майкрософт
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68f3006104b50876f6d2716ff4eb1efe0a705284
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60057411"
---
# <a name="how-to-create-a-product-manifest"></a>Практическое руководство. Создание манифеста продукта
Чтобы развернуть необходимые условия для приложения, можно создать пакет начального загрузчика. Пакет начального загрузчика содержит один файл манифеста продукта манифест пакета для каждого языкового стандарта. Манифест пакета содержит локализованные компоненты пакета. Сюда входят строки, условия лицензии и языковые пакеты.

 Дополнительные сведения о манифестах пакетов см. в разделе [как: создать манифест пакета](../deployment/how-to-create-a-package-manifest.md).

## <a name="create-the-product-manifest"></a>Создание манифеста продукта

#### <a name="to-create-the-product-manifest"></a>Создание манифеста продукта

1. Создайте каталог для пакета начального загрузчика. В этом примере используется C:\package.

2. В Visual Studio создайте новый файл XML с именем *product.xml*и сохраните его для *C:\package* папки.

3. Добавьте следующий код XML для описания XML-код пространства имен и продукта для пакета. Замените код продукта с уникальным идентификатором для пакета.

    ```xml
    <Product
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
    ProductCode="Custom.Bootstrapper.Package">
    ```

4. Добавьте XML-код, чтобы указать, что пакет имеет зависимость. В этом примере используется зависимость на Microsoft Windows Installer 3.1.

    ```xml
    <RelatedProducts>
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
      </RelatedProducts>
    ```

5. Добавьте XML-код, чтобы получить список всех файлов, находящихся в пакет начального загрузчика. В этом примере используется имя файла пакета *CorePackage.msi*.

    ```xml
    <PackageFiles>
        <PackageFile Name="CorePackage.msi"/>
    </PackageFiles>
    ```

6. Скопируйте или переместите *CorePackage.msi* файл *C:\package* папки.

7. Добавьте XML-код, чтобы установить пакет с помощью команд загрузчика. Загрузчик автоматически добавляет **/qn** флаг *.msi* файл, который будет установлен автоматически. Если файл *.exe*, загрузчик запускает *.exe* файла с помощью оболочки. Следующий код XML показывает без аргументов для *CorePackage.msi*, но вы можете поместить аргумент командной строки в `Arguments` атрибута.

    ```xml
    <Commands>
        <Command PackageFile="CorePackage.msi" Arguments="">
    ```

8. Добавьте следующий XML-код, проверьте, установлены ли этот пакет начального загрузчика. Замените код продукта с идентификатором GUID для распространяемого компонента.

    ```xml
    <InstallChecks>
        <MsiProductCheck
            Property="IsMsiInstalled"
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
    </InstallChecks>
    ```

9. Добавьте XML-код, чтобы изменить поведение загрузчика в зависимости от того, если уже установлен компонент загрузчика. Если компонент установлен, пакет начального загрузчика не выполняется. Следующий XML-код проверяет, является ли текущий пользователь администратором, так как этот компонент требует полномочий администратора.

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

10. Добавьте XML-код для задания кодов выхода, если установка прошла успешно, и если необходима перезагрузка. Следующий код XML показано, как завершится неудачей и FailReboot выйти из кодов, которые указывают, что загрузчик не продолжит установку пакетов.

    ```xml
    <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
    </ExitCodes>
    ```

11. Добавьте следующий XML-код, чтобы завершить раздел команд загрузчика.

    ```xml
        </Command>
    </Commands>
    ```

12. Переместить *C:\package* папки в каталог начального загрузчика Visual Studio. Для Visual Studio 2010, это *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* каталога.

## <a name="example"></a>Пример
 Манифест продукта содержит инструкции по установке для пользовательских предварительные требования.

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
- [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)