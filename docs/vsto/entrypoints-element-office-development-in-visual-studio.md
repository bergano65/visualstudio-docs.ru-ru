---
title: '&lt;entryPoints&gt; элемент (Разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoints> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8392fa83899e078050786091fa4a2f462eb40c9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852947"
---
# <a name="ltentrypointsgt-element-office-development-in-visual-studio"></a>&lt;entryPoints&gt; элемент (Разработка решений Office в Visual Studio)
  Элемент `entryPoints` пространства имен `vstav3` содержит все элементы `entryPoint` , связанные с решением Office.

## <a name="syntax"></a>Синтаксис

```xml
<entryPoints>
    <entryPoint>
    </entryPoint>
    <entryPoint>
    </entryPoint>
    <entryPoint>
    </entryPoint>
</entryPoints>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `entryPoints` является обязательным и находится в пространстве имен `vstav3` . В манифесте приложения определяется один элемент `entryPoints` для каждого решения Office. Например, при развертывании трех решений Office в многопроектном развертывании в манифесте приложения будет существовать три элемента `entryPoints` .

 Элемент `entryPoints` имеет указанный ниже атрибут.

|Атрибут|Описание|
|---------------|-----------------|
|id|Требуется для многопроектного развертывания. Имя решения Office. Идентификатор не может содержать знак равенства (=).|

 У элемента`entryPoints` имеются перечисленные ниже элементы.

### <a name="entrypoint"></a>entryPoint
 Обязательный. Роль `entryPoint` элемент в `vstav3` пространство имен определяется в [ &#60;entryPoint&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md).

## <a name="document-level-customization-example"></a>Пример настройки на уровне документа

### <a name="description"></a>Описание:
 В приведенном ниже примере кода показан элемент `entryPoints` в манифесте приложения для решения на уровне документа, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstav3:entryPoints>
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
</vstav3:entryPoints>
```

## <a name="vsto-add-in-example"></a>Пример надстройки VSTO

### <a name="description"></a>Описание:
 В приведенном ниже примере кода показан элемент `entryPoints` манифеста приложения для решения на уровне приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstav3:entryPoints>
  <vstav3:entryPoint
    class="ContosoOutlookAddIn.ThisAddIn">
    <assemblyIdentity
      name="ContosoOutlookAddIn"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
</vstav3:entryPoints>
```

## <a name="multi-project-deployment-example"></a>Пример развертывания нескольких проектов

### <a name="description"></a>Описание:
 В приведенном ниже примере кода показан элемент `entryPoints` в манифесте приложения для многопроектного развертывания. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstav3:entryPoints
  id="ContosoExcel">
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
</vstav3:entryPoints>
<vstav3:entryPoints
  id="ContosoOutlook">
  <vstav3:entryPoint
    class="ContosoOutlookAddIn.ThisAddIn">
    <assemblyIdentity
      name="ContosoOutlookAddIn"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
</vstav3:entryPoints>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)