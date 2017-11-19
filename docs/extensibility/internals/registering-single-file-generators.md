---
title: "Регистрация генераторы одиночных файлов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9c75258f24ba86b1ff8d2f3fcd4a16cc4faf5c1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="registering-single-file-generators"></a>Регистрация генераторы одиночных файлов
Чтобы сделать доступным пользовательский инструмент [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], необходимо зарегистрировать его таким образом [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] можно создать его экземпляр и связывает его с определенным типом проекта.  
  
### <a name="to-register-a-custom-tool"></a>Чтобы зарегистрировать пользовательский инструмент  
  
1.  Регистрация пользовательского инструмента DLL либо в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] локального реестра или в разделе HKEY_CLASSES_ROOT реестра системы.  
  
     Например, вот сведения о регистрации для управляемых MSDataSetGenerator пользовательский инструмент, который поставляется вместе с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  Создайте раздел реестра в нужной [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hive в генераторы\\*GUID* где *GUID* определяется GUID системы проекта конкретного языка или службой. Имя ключа становится программное имя пользовательского средства. Ключ пользовательское средство имеет следующие значения:  
  
    -   (Значение по умолчанию)  
  
         Необязательно. Предоставляет понятное описание пользовательского инструмента. Этот параметр является обязательным, но рекомендуется.  
  
    -   CLSID  
  
         Обязательный. Указывает идентификатор библиотеки классов из COM-компонент, реализующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.  
  
    -   GeneratesDesignTimeSource  
  
         Обязательный. Указывает ли типы из файлов, созданных этот пользовательский инструмент, становятся доступными для визуальных конструкторов. Значение этого параметра требуется для типов, не доступен для визуальных конструкторов (нуль) 0 или 1 (один) для типов, доступных для визуальных конструкторов.  
  
    > [!NOTE]
    >  Необходимо зарегистрировать пользовательский инструмент отдельно для каждого языка, для которого требуется пользовательский инструмент доступен.  
  
     Например MSDataSetGenerator регистрируется один раз для каждого языка:  
  
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
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Реализация генераторы одного файла](../../extensibility/internals/implementing-single-file-generators.md)   
 [Предоставление типов для визуальных конструкторов](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Введение на BuildManager объект](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)