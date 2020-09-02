---
title: Регистрация генераторов одного файла | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6afcd708ac50a46ceb3359f0d2c0821e3b788f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696105"
---
# <a name="registering-single-file-generators"></a>Регистрация генераторов одного файла
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Чтобы сделать пользовательский инструмент доступным в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , необходимо зарегистрировать его, чтобы он [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] мог создать экземпляр и связать его с определенным типом проекта.  
  
### <a name="to-register-a-custom-tool"></a>Регистрация пользовательского средства  
  
1. Зарегистрируйте библиотеку DLL пользовательских средств либо в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] локальном реестре, либо в системном реестре в разделе HKEY_CLASSES_ROOT.  
  
     Например, ниже приведены сведения о регистрации для управляемого пользовательского инструмента Мсдатасетженератор, который поставляется вместе с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] :  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2. Создайте раздел реестра в нужном [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] кусте под \\ *идентификатором GUID* генераторов, где *GUID* — это идентификатор GUID, определенный системой или службой проекта конкретного языка. Имя ключа превращается в программное имя пользовательского инструмента. Пользовательский ключ инструмента имеет следующие значения:  
  
    - (по умолчанию)  
  
         Необязательный элемент. Предоставляет понятное описание пользовательского инструмента. Этот параметр является необязательным, но рекомендуется.  
  
    - CLSID  
  
         Обязательный. Задает идентификатор библиотеки классов COM-компонента, реализующего интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .  
  
    - женератесдесигнтимесаурце  
  
         Обязательный. Указывает, доступны ли типы из файлов, созданных этим пользовательским инструментом, в визуальных конструкторах. Значение этого параметра должно быть (ноль) 0 для типов, недоступных для визуальных конструкторов или (один) 1 для типов, доступных для визуальных конструкторов.  
  
    > [!NOTE]
    > Пользовательское средство необходимо зарегистрировать отдельно для каждого языка, для которого необходимо, чтобы пользовательский инструмент был доступен.  
  
     Например, Мсдатасетженератор регистрируется один раз для каждого языка:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Реализация генераторов с одним файлом](../../extensibility/internals/implementing-single-file-generators.md)   
 [Определение пространства имен по умолчанию для проекта](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Предоставление типов для визуальных конструкторов](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Знакомство с объектом BuildManager](https://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
