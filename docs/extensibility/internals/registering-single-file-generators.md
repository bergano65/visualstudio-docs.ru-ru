---
title: "Регистрация генераторов одного файла | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 239f68b8bdbaf910f25b9fbe6e0fdd7061fe0f16
ms.lasthandoff: 02/22/2017

---
# <a name="registering-single-file-generators"></a>Регистрация генераторов одного файла
Чтобы сделать доступными в пользовательское средство [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], необходимо зарегистрировать так [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] можно создать его экземпляр и связывает его с определенным типом проекта.  
  
### <a name="to-register-a-custom-tool"></a>Чтобы зарегистрировать пользовательский инструмент  
  
1.  Регистрация пользовательского инструмента DLL либо в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] локального реестра или в реестре в кусте реестра HKEY_CLASSES_ROOT.  
  
     Например, вот сведения о регистрации для управляемых MSDataSetGenerator пользовательский инструмент, который поставляется вместе с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  Создайте раздел реестра в нужной [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hive под генераторы\\*GUID* где *GUID* определяется GUID конкретного языка системы проекта или службой. Имя ключа становится программное имя пользовательского средства. Пользовательский инструмент ключ имеет следующие значения:  
  
    -   (Значение по умолчанию)  
  
         Необязательный. Понятное описание пользовательского инструмента. Этот параметр является обязательным, но рекомендуется.  
  
    -   CLSID  
  
         Обязательный. Указывает идентификатор библиотеки классов из COM-компонент, реализующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
  
    -   GeneratesDesignTimeSource  
  
         Обязательный. Указывает ли типы из файлов, созданных этот пользовательский инструмент, становятся доступными для визуальных конструкторов. Значение этого параметра должно быть (нуль) 0 для типов, не доступен для визуальных конструкторов или 1 (один) для типов, доступных для визуальных конструкторов.  
  
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
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator></xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Реализация генераторов одного файла](../../extensibility/internals/implementing-single-file-generators.md)   
 [Определение пространства имен по умолчанию проекта](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Предоставление визуальные конструкторы типов](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Знакомство с объектом BuildManager](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
