---
title: "Практическое руководство. Создание манифеста пакета | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "зависимости, пакеты пользовательского загрузчика"
  - "файлы пакета [ClickOnce]"
  - "файлы пакета [установщик Windows]"
  - "необходимые компоненты, пакет пользовательского загрузчика"
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Практическое руководство. Создание манифеста пакета
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Для развертывания компонентов, требуемых для работы приложения, можно создать пакет загрузчика.  Пакет загрузчика содержит один файл манифеста продукта для каждого языкового стандарта.  В манифесте продукта должны содержаться общие функциональные возможности для различных локализованных версий продукта.  
  
 Дополнительные сведения о манифестах пакетов см. в разделе [Практическое руководство. Создание манифеста продукта](../deployment/how-to-create-a-product-manifest.md).  
  
## Создание манифеста пакета  
  
#### Процедура создания манифеста пакета  
  
1.  Создайте каталог для пакета загрузчика.  В данном примере используется каталог "C:\\package".  
  
2.  Создайте подкаталог с именем, соответствующим языковому стандарту, например каталог en для английской версии.  
  
3.  В Visual Studio создайте XML\-файл `package.xml` и сохраните его в папке "C:\\package\\en".  
  
4.  Чтобы указать имя пакета загрузчика, язык и региональные параметры для этого локализованного манифеста пакета и условие лицензии \(последнее указывать необязательно\), добавьте следующий XML\-код.  В приведенном ниже примере XML\-кода используются переменные `DisplayName` и `Culture`, которые будут описаны далее.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Чтобы указать файлы, содержащиеся в каталоге для конкретного языкового стандарта, добавьте следующий XML\-код.  В этом примере XML\-кода используется файл eula.txt, который предназначен для языкового стандарта **en**.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Чтобы добавить локализуемые строки в пакет загрузчика, добавьте следующий XML\-код.  В приведенном ниже примере XML\-кода добавляются строки ошибок для языкового стандарта en.  
  
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
  
7.  Скопируйте папку "C:\\package" в каталог загрузчика Visual Studio.  Каталог загрузчика в Visual Studio 2010: \\Program Files\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages.  
  
## Пример  
 Манифест пакета содержит данные для конкретного языкового стандарта, такие как сообщения об ошибках, условия лицензии на ПО и языковые пакеты.  
  
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
  
## См. также  
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)