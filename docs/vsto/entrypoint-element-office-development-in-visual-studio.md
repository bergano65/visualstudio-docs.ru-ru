---
title: '&lt;&gt;элемент entryPoint (разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 17f57b90b7c6aa4c254b2b55ee838a3086193ef7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543602"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;&gt;элемент entryPoint (разработка решений Office в Visual Studio)
  Каждый элемент `entryPoint` пространства имен `vstav3` идентифицирует сборку настройки, которая должна запускаться при установке этого приложения [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .

## <a name="syntax"></a>Синтаксис

```xml
<entryPoint class>
    <assemblyIdentity />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `entryPoint` является обязательным и находится в пространстве имен `vstav3` .

 Каждый элемент `entryPoint` может содержать только одну сборку настройки. Может существовать несколько элементов `entryPoint` , определенных в манифесте приложения.

 Элемент `entryPoint` имеет перечисленные ниже атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`class`|Обязательный. Идентифицирует сборку настройки для выполнения. Синтаксис для этого атрибута: *ИмяПространстваИмен.ИмяКласса*.|

 Объект`entryPoint` имеет следующий элемент.

### <a name="assemblyidentity"></a>assemblyIdentity
 Обязательный. Элемент `assemblyIdentity` в пространстве имен `vstav3` ссылается на существующий элемент `assemblyIdentity` в манифесте приложения [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .

 Роль `assemblyIdentity` и ее атрибуты определены в [&#60;assemblyIdentity&#62; элементе &#40;ClickOnce Application&#41;](../deployment/assemblyidentity-element-clickonce-application.md).

## <a name="document-level-customization-example"></a>Пример настройки на уровне документа

### <a name="description"></a>Описание
 В приведенном ниже примере кода показан элемент `entryPoint` в манифесте приложения для решения Office уровня документа, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstav3:entryPoint
  class="ContosoExcelWorkbook.ThisWorkbook">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet1">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet2">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet3">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="vsto-add-in-example"></a>Пример надстройки VSTO

### <a name="description"></a>Описание
 В приведенном ниже примере кода показан элемент `entryPoint` в манифесте приложения для решения Office уровня приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstav3:entryPoint
  class="ContosoOutlookAddIn.ThisAddIn">
  <assemblyIdentity
    name="ContosoOutlookAddIn"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)