---
title: Регистрация генераторов единого файла (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cea2ebba4739695393447a36e9842ade1670954
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705810"
---
# <a name="registering-single-file-generators"></a>Регистрация генераторов одного файла
Чтобы сделать пользовательский [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]инструмент доступным в, вы должны зарегистрировать его, чтобы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] можно мгновенно его и связывает его с определенным типом проекта.

### <a name="to-register-a-custom-tool"></a>Регистрация пользовательского инструмента

1. Зарегистрируйте пользовательский инструмент [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DLL либо в местном реестре, либо в системном реестре, под HKEY_CLASSES_ROOT.

    Например, вот регистрационная информация для управляемого пользовательского инструмента [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]MSDataSetGenerator, который поставляется с:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Создайте ключ реестра [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] в желаемом улье под генераторами\\*GUID,* где GUID является *GUID,* определяемым проектной системой или службой конкретного языка. Название ключа становится программным названием вашего пользовательского инструмента. Пользовательский ключ инструмента имеет следующие значения:

   - (по умолчанию)

        Необязательный параметр. Предоставляет удобное описание пользовательского инструмента. Этот параметр является необязательным, но рекомендуется.

   - CLSID

        Обязательный элемент. Определяет идентификатор библиотеки классов компонента <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>COM, который реализует.

   - ГенерируетДизайнДизайнTimeSource

        Обязательный элемент. Указывает, доступны ли визуальные дизайнеры типам файлов, созданных этим пользовательским инструментом. Значение этого параметра должно быть (ноль) 0 для типов, недоступных для визуальных дизайнеров или (один) 1 для типов, доступных для визуальных дизайнеров.

   > [!NOTE]
   > Вы должны зарегистрировать пользовательский инструмент отдельно для каждого языка, для которого вы хотите, чтобы пользовательский инструмент был доступен.

    Например, MSDataSetGenerator регистрируется один раз для каждого языка:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]
   @="Microsoft VB Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]
   @="Microsoft C# Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001
   ```

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [Реализация генераторов одного файла](../../extensibility/internals/implementing-single-file-generators.md)
- [Предоставление типов конструкторам визуальных элементов](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [Знакомство с объектом BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
