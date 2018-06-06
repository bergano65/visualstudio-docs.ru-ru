---
title: '&lt;RelatedProducts&gt; элемент (загрузчик) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5701b88f3942301c8fdb6d674fc323e62a93589b
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815461"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; элемент (загрузчик)
`RelatedProducts` Элемент определяет другие продукты, которые зависят от или включены в текущего продукта.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `RelatedProducts` Элемент является дочерним элементом `Product` элемента. Он не имеет атрибутов.  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 `DependsOnProduct` Элемент указывает, что текущего продукта зависит от данного продукта, и что данного продукта должен быть установлен до текущего. Он является дочерним элементом `RelatedProducts` элемента. Объект `RelatedProducts` элемент может иметь один или несколько `DependsOnProduct` элементов.  
  
 `DependsOnProduct` имеет следующий атрибут.  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|`Code`|Кодовое имя включенного продукта, в соответствии с `ProductCode` атрибут `Product` элемента. Дополнительные сведения см. в разделе [ \<продукта > элемент](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 `EitherProducts` Элемент определяет ноль или более `DependsOnProduct` элементов, и не имеет атрибутов. По крайней мере один `DependsOnProduct` в этом наборе необходимо предварительно установить текущего продукта. Объект `RelatedProducts` элемент может иметь ноль или более `EitherProducts` элементов.  
  
## <a name="includesproduct"></a>IncludesProduct  
 `IncludesProduct` Элемент указывает, входит в состав текущая установка продукта и отдельная установка не требуется. Он является дочерним элементом `RelatedProducts` элемента. Объект `RelatedProducts` элемент может иметь один или несколько `IncludesProduct` элементов.  
  
 `IncludesProduct` имеет следующий атрибут.  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|`Code`|Кодовое имя включенного продукта, в соответствии с `ProductCode` атрибут `Product` элемента. Дополнительные сведения см. в разделе [ \<продукта > элемент](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Пример  
 В следующем примере кода указывает, что установщик Microsoft устанавливается вместе с [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]и поэтому не требует отдельной установки.  
  
```xml  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>См. также  
 [\<Продукта > элемент](../deployment/product-element-bootstrapper.md)